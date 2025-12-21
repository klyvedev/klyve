---
layout: default
title: Quality Assurance
parent: User Documentation
nav_order: 5
---

# Quality Assurance
{: .fs-9 }

On-demand validation tools for continuous stability.
{: .fs-6 .fw-300 }

---

## 1. The Testing Philosophy
While Klyve enforces mandatory quality gates at the end of a sprint, you often need to run ad-hoc checks during development. Configure all on-demand test commands via the **Project > Testing** menu. Klyve does the rest of the work.

<div align="center" markdown="1">

| Testing Phase | Script Source (Who writes the code?) | Execution Source (Who presses the button?) | Test Runner Command Source (Where is the command defined?) |
| :--- | :---: | :---: | :--- |
| **Unit Testing** | Klyve | Klyve | Project Settings <br> Field: "Test Execution Command" |
| **Backend Regression** | Klyve | Klyve | Project Settings <br> Field: "Backend Regression Test Command" (Re-uses Unit Test setting) |
| **Backend Integration** | Klyve | Klyve | Klyve <br> "Backend Integration Test Command" or internally generated for the temporary script. |
| **Automated UI** | Klyve | Klyve | Project Settings <br> Field: "Automated UI Test Command" |
| **Manual UI** | Klyve (Writes Test Plan doc) | User | N/A <br> (Human execution) |

</div>

---

## 2. Backend Validation
Validates logic, API, and database layers without spinning up the UI.

### Initiate Integration Testing
Useful for a quick "Health Check" of the entire backend.
* **Prerequisite:** A valid "Backend Integration Test Command" must be configured in *Project Settings*.
* **Action:** Generates and triggers a full backend test suite for the sprint in the background.
* **Outcome:** Generates a formal **Integration Test Report** in `docs/test_reports/`.

### Initiate Regression Testing (Targeted)
Useful for verifying a specific bug fix or running a set of unit tests.
* **Flexibility:** Unlike the Integration check, you can override the command during test environment setup or by setting it via the project settings menu.
* **Action:** The system pre-populates your default command but allows edits (e.g., appending `-k "test_login_failure"` to run a single case).
* **Outcome:** Runs the specific command and logs results to project history.

---

## 3. Front-End Validation
Available only for projects flagged as **GUI Projects**.

### Generate Manual UI Test Plan
Useful for visual QA or when automated testing is too brittle.
* **Action:** Klyve analyzes your approved **UX/UI Specification**.
* **Outcome:** Generates a human-readable **Manual Test Checklist** (Markdown/Docx). You can download this file, perform the verification, and upload results later.

### Initiate Automated UI Testing
Useful for end-to-end regression of the interface.
* **Prerequisite:** A valid "UI Test Command" (e.g., Selenium, Playwright) must be configured in *Project Settings*.
* **Action:** Klyve generates the tests and executes the UI runner in a background process.
* **Outcome:** Parses the runner's raw output to produce an **Automated Front-End Test Report**.

---

## 4. Configuration
Navigate to **Project > Project Settings** to define your test runners.

* **Backend Regression Testing Command:** The default command for a suite of unit tests (e.g., `pytest`).
* **Backend Integration Command:** The default command for backend integration tests.
* **Automated UI Test Command:** The default command for GUI drivers that were setup during the Test Environment Setup phase.
* **Test Environment Setup:** You can review the setup checklist generated during the project's initialization at any time in the *Documents* section. (Use the "Save to .docx" option to create the checklist document during the Dev and Test Environment Setup phase).
