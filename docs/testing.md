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
Klyve treats testing as a continuous activity, not just a sprint phase. While the "Factory" enforces mandatory quality gates at the end of a build, you often need to run ad-hoc checks during development—for example, to verify a manual fix or check environmental stability.

Configure all on-demand test commands via the **Project > Testing** menu.

---

## 2. Backend Validation
These tests validate your application's logic, API, and database layers without spinning up the UI.

### Initiate Integration Testing
Useful for a quick "Health Check" of the entire backend.
* **Navigation:** *Project > Testing > Initiate Integration Testing*
* **Prerequisite:** A valid "Backend Integration Test Command" must be configured in *Project > Project Settings*. You must prepare and have your test tools and test scripts ready.
* **Action:** Triggers the full backend test suite in the background.
* **Outcome:**
    * Executes the configured command (e.g., `pytest tests/integration`).
    * Generates a formal **Integration Test Report** in `docs/test_reports/`, detailing pass/fail status for every module.

### Initiate Regression Testing (Targeted)
Useful for verifying a specific bug fix in a sprint or running a focused subset of tests.
* **Navigation:** *Project > Testing > Initiate Regression Testing*
* **Flexibility:** Unlike the Integration check, this command can be overriden during the test environment setup workflow when it pauses to ask for it.
    * If no command has already been entered and saved in the Project Settings, the system pre-populates your default test command but allows you to edit it (e.g., appending `-k "test_login_failure"` to run a single test case).
* **Outcome:** Runs the specific command and logs the results to the project history.

---

## 3. Front-End Validation
These options are available only if your project is flagged as a **GUI Project**.

### Generate Manual UI Test Plan
Useful for visual QA or when automated UI testing is too brittle.
* **Navigation:** *Project > Testing > Generate Manual UI Test Plan*
* **System Behavior:** Klyve analyzes your approved **UX/UI Specification** and generates a comprehensive, human-readable checklist.
* **Outcome:** A formatted Manual Test Plan (Markdown/Docx) is saved to your documents folder, listing every user journey, expected behavior, and pass/fail criteria. You can upload the updated document (with your test results) later.

### Initiate Automated UI Testing
Useful for end-to-end regression of the interface.
* **Navigation:** *Project > Testing > Initiate Automated UI Testing*
* **Prerequisite:** A valid "UI Test Command" (e.g., Selenium, Playwright, or PyTest-Qt instructions) must be configured in *Project > Project Settings*.
* **Action:** You need to prepare ready your test tools and scripts. Klyve executes the UI runner in a background process.
* **Outcome:** It parses the runner's raw output and correlates it with your specs to produce an **Automated Front-End Test Report**.

---

## 4. Configuration
To define the commands used by these workflows, navigate to **Project > Project Settings**.

* **Backend Integration Command:** The default command for logic tests.
* **Automated UI Test Command:** The default command for GUI drivers.
* **Test Environment Setup:** You can save the setup checklist generated during the project's test environment setup phase and review it at any time in the *Documents*.