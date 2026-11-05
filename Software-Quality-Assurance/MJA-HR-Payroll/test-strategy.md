---

```markdown
# Test Strategy — MJA-HR-PAYROLL

## 1. Strategy Objectives
The objective of this testing strategy is to define the QA methodology, boundary limits, and validation criteria for the Attendance and Borongan Payroll modules. The primary focus is verifying **zero financial calculation error**, robust **data integrity**, and user-safe **exception handling**.

---

## 2. Risk-Based Testing Matrix

| Risk ID | Feature / Flow | Failure Impact | Risk Level | Mitigation & Verification Technique |
|:---:|---|---|:---:|---|
| **R-01** | Borongan Salary Summation | Incorrect employee payment, financial auditing discrepancy | **Critical** | Mathematical model parity testing; item-by-item calculation cross-checks. |
| **R-02** | Unpaid Date Exclusions | Double counting or failure to deduct unpaid dates from net pay | **High** | Delta calculation verification (State Before vs. State After exclusion). |
| **R-03** | Missing Input Validation | Database integrity errors, partial/corrupted record creation | **High** | Negative testing; Boundary Value Testing (BVT); form integrity auditing. |
| **R-04** | Internal Schema Leakage | Exposure of database table columns and backend request keys | **Medium** | Payload fuzzing; input format rejection verification; toast audit. |

---

## 3. Test Design Techniques Applied

### 3.1. Mathematical & Business Logic Verification (Payroll)
Every calculated field was verified against the business domain formula:
$$\text{Quantity per baris} = \text{FD} + \text{ACT Rej.} + \text{Good MC}$$
$$\text{Bayaran Item} = \text{Quantity per baris} \times \text{Upah Pekerja}$$
$$\text{Net Salary Borongan} = \sum (\text{Bayaran Item}) + \text{Allowances} - \text{Deductions}$$

* **Precision Standard:** Verified to the exact unit without floating-point precision loss.
* **Exclusion Mechanism:** Verifying state persistence where excluding a record reduces the sum strictly by the excluded row's earned amount, and restoring recalculates the baseline total with zero residual drift.

### 3.2. Equivalence Partitioning & Boundary Value Analysis (Attendance)
* **Partitions:**
  * Valid, completely filled attendance logs (Valid).
  * Missing one mandatory field (Invalid / Negative).
  * Out-of-bounds timestamps and invalid format inputs (Negative).

---

## 4. Test Environment & Prerequisites

* **User Roles:** HRD / PIC (Authorized to manage bulk attendance and trigger payroll runs).
* **Browsers:** Google Chrome (Primary), Mozilla Firefox (Cross-engine compatibility).
* **Environment:** Staging / Pre-production testing instance with seeded employee master records and rate definitions.

---

## 5. Defect Severity & Priority Classification

| Level | Definition | Example in this Scope |
|---|---|---|
| **Critical (P0/P1)** | Halts core payroll run; incorrect monetary calculation; data loss. | Borongan item wage fails to multiply correctly by rate. |
| **High (P1/P2)** | Feature broken with no workaround; exclusion fails to subtract. | Unpaid date exclusion does not update total net pay. |
| **Medium (P2/P3)** | Function works, but displays technical backend errors or poor UX. | Internal validation keys exposed in error toast (`ATC-002`). |
| **Low (P3)** | Cosmetic flaw, alignment issue, or minor typos. | Label misalignments or spacing inconsistencies on payslip views. |

---

## 6. Entry and Exit Criteria

### Entry Criteria
* Seeded employee and Borongan rate data is active in the test environment.
* Role-based access control (RBAC) permits HRD/PIC access to the Attendance and Payroll menus.
* Test cases reviewed and finalized against business requirement documents.

### Exit Criteria
* 100% execution of high and critical priority test cases.
* 0 open Critical or High severity defects.
* All mathematical formulas confirmed with 100% calculation parity between manual independent models and system outputs.
* All identified medium defects documented with steps to reproduce and assigned to the development board.
