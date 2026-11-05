
# MJA-HR-PAYROLL — Quality Assurance Case Study

## Executive Overview
The **MJA-HR-PAYROLL** module is a core enterprise component responsible for daily attendance verification and piece-rate (**Borongan**) payroll settlement. 

Because payroll directly impacts legal labor compliance, employee trust, and operational financial accuracy, this testing cycle focused on business logic validation, state transitions, calculation integrity, and input sanitization to eliminate financial calculation drift and internal system data exposure.

---

## Scope Under Test

| Module | Core Functionality | Primary Risk Factors |
|---|---|---|
| **Daily Attendance (`Absensi`)** | Shift check-in/out, missing field handling, bulk actions, and date tracking. | Incomplete logs, database inconsistency, unhandled exception leaks. |
| **Borongan Payroll Engine** | Item-level wage calculation (`FD`, `ACT Rej.`, `Good MC`), dynamic date exclusions, and payslip generation. | Rounding drift, formula mismatches, retroactive calculation corruption. |

---

## Test Execution Summary

| Metric | Total |
|---|---|
| **Total Test Scenarios** | 12 |
| **Passed** | 10 |
| **Failed** | 2 |
| **Blocked** | 0 |
| **Defect Severity Distribution** | 1 Medium (Data Exposure / Localization), 1 Low (UI Alignment) |

---

## Key Findings & Defect Insights

### 1. Raw Backend Attribute Exposure (`ATC-002`)
* **Finding:** When mandatory attendance parameters were omitted during bulk entry, the application blocked the transaction but returned raw framework key paths (`data.6329.jam_aktual`) rather than localized UI labels (`Jam Aktual`).
* **Impact:** Information disclosure of internal database/request schema and poor user experience.
* **Remediation Note:** Form request validation mapped to localized language files (e.g., `id/validation.php`) with human-readable attribute aliases.

### 2. Exclusion Dynamic Recalculation (`PAYTC-002`)
* **Finding:** Unpaid date exclusions dynamically recalculated item earnings and baseline take-home amounts accurately without persistence side effects or orphaned production tallies.

---

## Repository Structure

```text
MJA-HR-PAYROLL/
├── README.md                  # Project overview, test metrics, and findings
├── test-strategy.md           # Strategic approach, risk matrix, and test methodologies
├── attendance-test-cases.md   # Functional & negative attendance test specifications
├── payroll-test-cases.md      # Financial formula, calculation, and exclusion suites
└── Screenshots/               # Execution evidence and error reproduction artifacts
    ├── attendance/
    └── Payroll/
