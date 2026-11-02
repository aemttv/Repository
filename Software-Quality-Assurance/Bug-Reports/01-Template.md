# Login & Registration – Bug Reports

## 1. Project Overview

| Information | Details |
|---|---|
| Project | Login & Registration Testing |
| Application | Sample Web Application |
| Testing Type | Manual Testing |
| Testing Approach | Black Box Testing |
| Author | Sani Alim |
| Report Type | Sample Bug Report Templates |

### Objective

This document provides a structured format for reporting software defects identified during login and registration testing.

Each bug report contains sufficient information to help developers understand, reproduce, investigate, and resolve the reported issue.

**Note:** The bug reports below are illustrative examples for portfolio documentation. They are not confirmed defects from an actual application.

---

## 2. Bug Report Template

| Field | Description |
|---|---|
| Bug ID | Unique identifier for the reported defect |
| Bug Title | Short description of the issue |
| Module | Affected application module |
| Severity | Impact of the defect on application functionality |
| Priority | Urgency of fixing the defect |
| Environment | Browser, operating system, and application version |
| Preconditions | Conditions required before reproducing the issue |
| Steps to Reproduce | Sequential steps to trigger the defect |
| Test Data | Input values used during testing |
| Expected Result | Correct behavior expected from the application |
| Actual Result | Behavior observed during testing |
| Status | New / Open / In Progress / Fixed / Retest / Closed |
| Evidence | Screenshot, screen recording, or other supporting material |

---

## 3. Sample Bug Reports

### BUG-001 – Login accepts incorrect credentials

<details>
<summary>Bug Details</summary>

| Field | Details |
|---|---|
| Bug ID | BUG-001 |
| Bug Title | Login accepts incorrect password |
| Module | Login |
| Severity | Critical |
| Priority | High |
| Environment | Chrome / Windows 11 |
| Status | New (Example) |

**Description:**

The login functionality allows a user to authenticate using an incorrect password associated with a registered email address.

**Preconditions:**
- A registered user account exists.
- The user is on the login page.

**Steps to Reproduce:**

1. Navigate to the login page.
2. Enter a registered email address.
3. Enter an incorrect password.
4. Click the Login button.

**Test Data:**

- Email: registered@example.com
- Password: WrongPassword123!

**Expected Result:**

The application should reject the login attempt and display an appropriate authentication error message.

**Actual Result:**

The application successfully authenticates the user despite the incorrect password.

**Evidence:**

[Attach screenshot or screen recording here]

**Impact:**

Unauthorized authentication may compromise account security and expose user information.

</details>

---

### BUG-002 – Registration allows duplicate email addresses

<details>
<summary>Bug Details</summary>

| Field | Details |
|---|---|
| Bug ID | BUG-002 |
| Bug Title | Registration accepts an existing email address |
| Module | Registration |
| Severity | High |
| Priority | High |
| Environment | Chrome / Windows 11 |
| Status | New (Example) |

**Description:**

The registration form allows users to create an account using an email address that is already associated with an existing account.

**Preconditions:**
- An account with the specified email address already exists.
- The user is on the registration page.

**Steps to Reproduce:**

1. Navigate to the registration page.
2. Enter a valid name.
3. Enter an email address already registered in the application.
4. Enter a valid password.
5. Confirm the password.
6. Click the Register button.

**Test Data:**

- Name: Sani Alim
- Email: registered@example.com
- Password: ValidPass123!
- Confirm Password: ValidPass123!

**Expected Result:**

The application should prevent registration and display a message indicating that the email address is already registered.

**Actual Result:**

The application creates another account using the same email address.

**Evidence:**

[Attach screenshot or screen recording here]

**Impact:**

Duplicate accounts may cause authentication issues, data inconsistencies, and account management problems.

</details>

---

### BUG-003 – Registration accepts mismatched passwords

<details>
<summary>Bug Details</summary>

| Field | Details |
|---|---|
| Bug ID | BUG-003 |
| Bug Title | Registration does not validate password confirmation |
| Module | Registration |
| Severity | Medium |
| Priority | Medium |
| Environment | Chrome / Windows 11 |
| Status | New (Example) |

**Description:**

The registration form allows users to submit the registration form even when the password and confirmation password fields contain different values.

**Preconditions:**
- The user is on the registration page.
- All other required fields contain valid information.

**Steps to Reproduce:**

1. Navigate to the registration page.
2. Enter a valid name.
3. Enter a valid email address.
4. Enter a password.
5. Enter a different value in the confirmation password field.
6. Click the Register button.

**Test Data:**

- Name: Sani Alim
- Email: new@example.com
- Password: ValidPass123!
- Confirm Password: DifferentPass123!

**Expected Result:**

The application should prevent registration and display a password mismatch validation message.

**Actual Result:**

The application proceeds with registration despite the mismatched password values.

**Evidence:**

[Attach screenshot or screen recording here]

**Impact:**

Users may experience confusion when attempting to log in because the password they intended to confirm does not match the registered password.

</details>

---

## 4. Bug Summary

| Bug ID | Module | Severity | Priority | Status |
|---|---|---|---|---|
| BUG-001 | Login | Critical | High | New (Example) |
| BUG-002 | Registration | High | High | New (Example) |
| BUG-003 | Registration | Medium | Medium | New (Example) |

**Note:** These are hypothetical examples. The summary must be updated based on actual testing results.

---

## 5. Severity Classification

| Severity | Description |
|---|---|
| Critical | Defect causes a major security risk, data compromise, or complete system failure. |
| High | Defect significantly affects important functionality. |
| Medium | Defect affects functionality but has a reasonable workaround. |
| Low | Minor issue with limited functional impact or cosmetic inconsistency. |

## 6. Priority Classification

| Priority | Description |
|---|---|
| High | Requires immediate attention and should be fixed as soon as possible. |
| Medium | Should be addressed in the normal development cycle. |
| Low | Can be scheduled for a later release. |

## 7. Bug Reporting Best Practices

- Use clear and descriptive bug titles.
- Include reproducible steps.
- Provide actual and expected results.
- Assign severity based on the impact of the defect.
- Assign priority based on the urgency of fixing the issue.
- Attach screenshots or recordings whenever possible.
- Update the bug status after retesting.

---

**Document Type:** Software Defect Documentation  
**Project:** Login & Registration Testing  
**Author:** Sani Alim
