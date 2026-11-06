### [BUG-001] Title: Raw Internal Field Attribute Is Displayed in Attendance Validation Message

- **Module / Component:** Daily Attendance (`Absensi`)
- **Severity / Priority:** Low Severity / Medium Priority
- **Environment:** Windows 11, Chrome v130+, App Version 1.0 (Commit `6c1be79`)
- **User Role:** Unit's PIC
- **Reported Date:** 30/10/2026
- **Related Test Case:** [ATC-002](https://github.com/aemttv/Repository/blob/main/Software-Quality-Assurance/MJA-HR-Payroll/Manual-Test-Suite/attendance-test-cases.md)

#### Description
When submitting the Daily Attendance form with a required field left empty, the application correctly prevents submission. However, the validation toast displays an internal field attribute (data.6329.jam_aktual) instead of a user-friendly field label.

This exposes an implementation-specific field path to the user rather than providing a clear validation message in Indonesian.

#### Steps to Reproduce
1. Log in using an authorized account.
2. Open the Daily Attendance page (Absensi).
3. Select the date containing the existing attendance record and choose the unit.
4. Select any test employee.
5. Choose `Absen` at the bulk action bar below.
6. Enter valid values in the other required fields.
7. Leave the `Jam Aktual` field empty while populating all other required fields.
8. Attempt to save the attendance.
9. Observe the resulting error toast notification.
10. Check whether an incomplete attendance record was created. 

#### Expected Result
- The application prevents submission when a required field is missing.
- A clear, user-friendly validation message is displayed using the corresponding UI field label.
- The message is presented in Indonesian.
- No incomplete attendance record is saved.

#### Actual Result
Form submission is halted, but the error toast surfaces unmapped framework validation keys:
> `"TERJADI KESALAHAN: The data.6329.jam_aktual field is required."`

#### Business & Technical Impact

**Business Impact:**
- Users may have difficulty identifying which field requires correction.
- The technical error message reduces the clarity and usability of the attendance form.
- Users may require additional assistance to understand the validation error.

**Technical Impact:**
- Information disclosure: exposes internal request structure (`data.<employee_id>.<attribute>`).
- Indicates missing attribute aliases in the backend validation layer (e.g., missing custom names in `attributes()` or localization dictionaries).

**Data Integrity:**
* Verified: The transaction successfully rolls back. No partial or corrupted attendance rows are written to the database.

#### Supporting Evidence

**Validation Error Toast**

![Validation Error Toast](Evidence/Attendance/ATC-002-error-msg.png)
