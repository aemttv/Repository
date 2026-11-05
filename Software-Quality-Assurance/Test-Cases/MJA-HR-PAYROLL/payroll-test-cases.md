# Payroll Test Cases

> **Project:** MJA Integrated HR & Payroll System  
> **Module:** Payroll

## PAYTC-001 — Verify Borongan Payroll Calculation

| Field | Details |
|---|---|
| Test scenario | Verify that the Net Salary Borongan payroll amount follows the configured calculation. |
| Test type | Calculation / Business logic |
| Priority | Critical |
| Preconditions | User is logged in with permission (HRD/PIC) to manage payroll. A worker has valid Borongan production and payroll data for the selected period. Applicable deductions and allowances(PKWT) are configured. |
| Test data | Use a controlled test record with known values for total Borongan wages, other payments, and allowances. |

**Test steps**
1. Log in using an authorized account.
2. Select Payroll.
3. Choose and select `PAYSLIP` on that unit.
4. Fill in the popup of the test worker's Borongan data and select `PROSES PAYROLL`.
5. Record the displayed total Borongan wages, other payments, and allowances.
6. Independently calculate the expected net salary using the formula below.
7. Compare the independently calculated amount with the application result.

**Expected result**

The net Borongan amount matches the configured formula:

`Quantity per baris = FD + ACT Rej. + Good MC`

`Bayaran Item = QtyPerBaris * Upah Pekerja`

`Net Salary Borongan = ∑Bayaran Item`

All figures should use the same period and applicable payroll rules.

**Actual result:**
- The displayed `Hasil Gaji` matches the manual independent calculation down to the exact currency precision (no rounding drift).
- All calculated items reflect only the production records and rates defined for the selected payroll period and unit.

**Status:** Pass

### Test Evidence

**Payroll Calculation Breakdown**

![PHP Payroll Calculation Breakdown](../Screenshots/attendance/PAYTC-001-calculation.png)


---

## PAYTC-002 — Exclude Unpaid Attendance Dates from Payroll

| Field | Details |
|---|---|
| Test scenario | Verify that dates selected as unpaid exclusions are not included in the payable attendance calculation. |
| Test type | Functional / Business logic |
| Priority | High |
| Preconditions | User is logged in with permission (HRD/PIC) to manage payroll. The selected worker has attendance and payroll data for the chosen period. The application provides an option to exclude unpaid dates. |
| Test data | Use a test worker with at least one date selected for exclusion and other payable dates in the same period. |

**Test steps**
1. Log in using an authorized account.
2. Select Payroll.
3. Choose and select `PAYSLIP` on that unit.
4. Select a period that has workers attendance data.
5. Select a date that should be excluded from payment and choose `PROSES PAYROLL`.
6. Compare the result with a manual calculation that excludes the selected date.
7. Independently calculate the expected net salary using the formula below.
8. Remove the exclusion date and recalculate again without the exclusion date.

**Expected result**
- Selecting the unpaid exclusion date and processing payroll successfully omitted the target date's attendance and production records from the summary.
- The calculated Net Salary Borongan / Hasil Gaji dynamically decreased to match the manual calculation excluding that date.
- Deselecting/removing the exclusion date and reprocessing restored the excluded date's records, returning the payroll amount to the original total.
- Both output states matched the expected values with zero discrepancy.

**Actual result:**
The application excluded production and attendance records for the selected date upon running PROSES PAYROLL, resulting in a lower net salary that matches the independent calculation. Removing the exclusion restored the date and recalculated the initial full salary correctly.

**Status:** Pass

### Test Evidence

**Payroll before exclusion**

![Payroll before exclusion](Software-Quality-Assurance/Test-Cases/MJA-HR-PAYROLL/Screenshots/Payroll/PAYTC-002-before-exclusion.png)

**Payroll after exclusion**

![Payroll after exclusion](Software-Quality-Assurance/Test-Cases/MJA-HR-PAYROLL/Screenshots/Payroll/PAYTC-002-after-exclusion.png)

---
