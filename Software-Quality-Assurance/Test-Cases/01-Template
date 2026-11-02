# Login & Registration – Test Cases

## 1. Project Overview

| Information | Details |
|---|---|
| Project | Login & Registration Testing |
| Application | Sample Web Application |
| Testing Type | Manual Testing |
| Testing Approach | Black Box Testing |
| Test Environment | Web Browser |
| Test Status | Not Executed (Template) |

### Testing Objective

The objective of this testing activity is to verify the functionality, input validation, and error handling of the login and registration modules.

Testing focuses on ensuring that users can successfully authenticate with valid credentials, register new accounts, and receive appropriate validation messages when submitting invalid or incomplete information.

---

## 2. Test Case Format

| Field | Description |
|---|---|
| Test Case ID | Unique identifier for each test case |
| Test Scenario | Functionality being tested |
| Preconditions | Conditions required before execution |
| Test Steps | Actions performed by the tester |
| Test Data | Input values used during testing |
| Expected Result | Expected system behavior |
| Actual Result | Observed system behavior |
| Status | Pass / Fail / Blocked / Not Executed |

---

## 3. Login Test Cases

**Module:** Login

**Preconditions:**
- User is on the login page.
- A registered user account exists.

| Test Case ID | Test Scenario | Test Steps | Test Data | Expected Result |
|---|---|---|---|---|
| LOGIN-001 | Login with valid credentials | Enter valid email and password, then click Login. | registered@example.com / ValidPass123! | User successfully logs in and is redirected to the appropriate page. |
| LOGIN-002 | Login with incorrect password | Enter a registered email and incorrect password. | registered@example.com / WrongPass123! | Login is rejected and an appropriate error message is displayed. |
| LOGIN-003 | Login with unregistered email | Enter an email that does not exist and a password. | unknown@example.com / ValidPass123! | Login is rejected and an appropriate error message is displayed. |
| LOGIN-004 | Submit empty fields | Leave both fields empty and click Login. | Email: Empty / Password: Empty | Required field validation is displayed. |
| LOGIN-005 | Submit empty email | Leave email empty and enter a password. | Email: Empty / Password: ValidPass123! | Email validation is displayed and login is prevented. |
| LOGIN-006 | Submit empty password | Enter a valid email and leave password empty. | registered@example.com / Empty | Password validation is displayed and login is prevented. |
| LOGIN-007 | Enter invalid email format | Enter an incorrectly formatted email and a password. | invalid-email / ValidPass123! | Email format validation is displayed. |
| LOGIN-008 | Enter email with leading/trailing spaces | Enter an email with surrounding spaces and a valid password. | " registered@example.com " / ValidPass123! | The application handles surrounding whitespace according to its input validation rules. |
| LOGIN-009 | Verify password masking | Enter a password into the password field. | ValidPass123! | Password characters are masked by default. |
| LOGIN-010 | Toggle password visibility | Enter a password and click the show/hide password control. | ValidPass123! | Password visibility changes correctly when toggled. |
| LOGIN-011 | Login with case variation in email | Enter the registered email using different letter casing. | REGISTERED@example.com / ValidPass123! | Email authentication follows the application's email case-handling rules. |
| LOGIN-012 | Login with SQL injection-like input | Enter SQL injection-like text into the email field. | ' OR '1'='1 / AnyPassword123! | Application does not bypass authentication or expose database errors. |
| LOGIN-013 | Verify password field length handling | Enter a password exceeding the application's supported maximum length. | Long password string | Application handles the input safely and follows its documented length rules. |

---

## 4. Registration Test Cases

**Module:** Registration

**Preconditions:**
- User is on the registration page.
- A valid email address is available for testing.
- The email used for duplicate testing already belongs to an existing account.

| Test Case ID | Test Scenario | Test Steps | Test Data | Expected Result |
|---|---|---|---|---|
| REG-001 | Register with valid information | Fill in all required fields and click Register. | New user / new@example.com / ValidPass123! | Account is successfully created and the appropriate confirmation is displayed. |
| REG-002 | Submit all fields empty | Leave all fields empty and click Register. | All fields empty | Required field validation is displayed. |
| REG-003 | Submit empty name | Leave the name field empty and complete the other fields. | Name: Empty | Name validation is displayed and registration is prevented. |
| REG-004 | Submit empty email | Leave email empty and complete the other fields. | Email: Empty | Email validation is displayed and registration is prevented. |
| REG-005 | Submit empty password | Leave password empty and complete the other fields. | Password: Empty | Password validation is displayed and registration is prevented. |
| REG-006 | Enter invalid email format | Enter an incorrectly formatted email. | invalid-email | Email format validation is displayed. |
| REG-007 | Register with existing email | Enter an email address already associated with an account. | registered@example.com | Registration is rejected with an appropriate duplicate email message. |
| REG-008 | Enter password below minimum length | Enter a password shorter than the minimum allowed length. | Abc12! | Password length validation is displayed. |
| REG-009 | Enter password without required complexity | Enter a password that does not satisfy the application's password policy. | password123 | Appropriate password validation is displayed. |
| REG-010 | Enter mismatched confirmation password | Enter different values in password and confirmation fields. | Password: ValidPass123! / Confirm: DifferentPass123! | Password mismatch validation is displayed. |
| REG-011 | Enter matching passwords | Enter identical values in password and confirmation fields. | ValidPass123! / ValidPass123! | Password confirmation is accepted. |
| REG-012 | Enter special characters in name | Enter special characters in the name field. | Sani @#$ Alim | Application handles input according to its name validation rules without errors. |
| REG-013 | Enter maximum-length name | Enter a name at the documented maximum length. | Maximum allowed characters | Input is accepted if within the defined limit. |
| REG-014 | Enter name exceeding maximum length | Enter a name exceeding the documented maximum length. | Maximum length + 1 character | Application prevents or safely validates the excessive input. |
| REG-015 | Submit registration multiple times | Click Register repeatedly using the same registration data. | Same email and registration data | Duplicate account creation is prevented. |
| REG-016 | Verify password masking | Enter a password into the registration password field. | ValidPass123! | Password characters are masked by default. |
| REG-017 | Verify registration with leading/trailing email spaces | Enter an email with surrounding whitespace. | " new@example.com " | Application handles whitespace consistently with its email validation rules. |

---

## 5. Test Execution Summary

**Execution Status:** Not Executed

| Module | Total Test Cases | Passed | Failed | Blocked | Not Executed |
|---|---:|---:|---:|---:|---:|
| Login | 13 | 0 | 0 | 0 | 13 |
| Registration | 17 | 0 | 0 | 0 | 17 |
| **Total** | **30** | **0** | **0** | **0** | **30** |

## 6. Testing Notes

- Expected results should be adjusted according to the application's actual requirements.
- Password policies and maximum input lengths must be confirmed before execution.
- Actual results must be recorded after performing each test case.
- Test cases should be marked Pass or Fail based on the observed results.
- Any unexpected behavior should be documented in a separate bug report.

---

**Document Type:** Manual Testing Documentation  
**Project:** Login & Registration Testing  
**Author:** Sani Alim
