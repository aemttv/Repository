# Defect & Incident Reports — QA Portfolio

## 1. Overview
This repository section contains structured defect reports identified during test execution cycles across system modules (including **MJA-HR-PAYROLL**). 

The goal of this defect management approach is to provide engineering and development teams with actionable, reproducible, and context-rich bug logs. Rather than simply describing surface UI behaviors, each report pinpoints:
* Exact environmental conditions and test data.
* Root cause assessment (client-side vs. API/backend validation vs. business logic).
* Potential business risk and customer impact.
* Concrete reproduction steps and non-sensitive evidentiary artifacts.

---

## 2. Defect Severity & Priority Governance

Defects are triaged using a two-dimensional classification model:

| Level | Severity (Technical & Functional Impact) | Priority (Business & Resolution Urgency) |
|:---:|---|---|
| **P0 / S1 (Critical)** | System crash, data corruption, calculation mismatch in financial records, blocker with no workaround. | Immediate hotfix / release blocker. |
| **P1 / S2 (High)** | Core workflow broken, logic failure (e.g., exclusion date not deducted), broken state transition. | Next scheduled sprint patch / milestone blocker. |
| **P2 / S3 (Medium)** | Non-critical functionality failure, validation leaks internal database schema, confusing UI/UX. | Addressed during stabilization or regular sprint cycles. |
| **P3 / S4 (Low)** | Minor cosmetic defects, UI alignment inconsistencies, minor copy/typographical errors. | Low urgency / backlog refinement. |

---

## 3. Logged Defect Inventory

| Defect ID | Module | Title / Issue Summary | Severity | Priority | Status | Related Test Case |
|:---:|:---:|---|:---:|:---:|:---:|:---:|
| **BUG-001** | Attendance | Raw backend validation parameter exposed in UI toast message | Medium | P2 | Open | `ATC-002` |

---

## 4. Defect Report Standard Template

Every submitted bug report follows a strict, repeatable specification:

```markdown
### [DEFECT-ID] Title: Brief, unambiguous summary of the unexpected behavior

- **Module / Component:** 
- **Severity / Priority:** 
- **Environment:** (OS, Browser, Build/Commit version, User Role)
- **Reported Date:** 

#### Description
A clear, objective narrative explaining what occurred versus what was expected from a domain perspective.

#### Steps to Reproduce
1. Step-by-step sequential instructions...
2. ...
3. ...

#### Expected Result
What the application should have done according to requirements and UI standards.

#### Actual Result
What the application actually did, highlighting specific discrepancies or leaked details.

#### Business & Technical Impact
Analysis of potential risk (e.g., security exposure, user friction, data corruption).

#### Supporting Evidence
Screenshots, network payload snippets, console logs, or recorded recordings.
```

---

## 5. Sample Highlight Report: BUG-001

### `BUG-001`: Raw Internal Field Attribute Is Displayed in Attendance Validation Message

* **Module:** Attendance (`Absensi`) — Bulk Action Form
* **Severity:** Medium (S3)
* **Priority:** P2
* **Found in Test Case:** `ATC-002`
* **Reporter:** Sani
* **Target Audience:** Frontend Team, Backend API Team

#### Problem Summary
During bulk attendance submission, leaving mandatory fields (such as `jam_aktual`) blank triggers an unformatted Laravel request validator string (`The data.6329.jam_aktual field is required.`) directly into the user toast popup instead of a localized, user-facing error message.

#### Root Cause Analysis (QA Assessment)
The backend validation pipeline uses raw nested payload keys (e.g., `data.*.jam_aktual`) in its validation rules without providing friendly attribute name mappings in the validation language translation files (e.g., `resources/lang/id/validation.php` attributes array). The frontend blindly renders the raw `error.response.data.message` without sanitizing or remapping it to the UI label.

#### Remediation Suggestion
1. **Backend:** Define custom attribute translations:
   ```php
   'attributes' => [
       'data.*.jam_aktual' => 'Jam Aktual',
   ],
   ```
2. **Frontend:** Implement standard fallback error handling to map error keys to form field labels, ensuring no internal indexing or raw column identifiers are displayed to the user.
