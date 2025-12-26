---
layout: default
title: Handling Failures
parent: User Documentation
nav_order: 4
---

# Handling Failures & Debugging
{: .fs-9 }

When the "Happy Path" ends, the engineering begins.
{: .fs-6 .fw-300 }

---

## 1. The Automated Triage Layer
Klyve acknowledges that code generation is probabilistic. It does not crash when a task fails; it enters a **Triage State**.

### Self-Correction
Before bothering you, the system attempts to fix the error automatically.
* **Logic:** It analyzes the stack trace and the failed test output.
* **Action:** It refactors the code or adjusts the test case.
* **Persistence:** It repeats this process up to the number of times defined in your **Max Debug Attempts** setting (*File > Settings*).

If the error persists beyond these attempts, the pipeline pauses and escalates to the **Debug Dashboard**.

---

## 2. Handling Environment Failures
These occur when the factory floor is missing a tool (e.g., `npm` not found, network timeout).

* **Option A: "I have fixed the issue, Retry"**
    * **Scenario:** You installed the missing dependency or restored internet access.
    * **Action:** Click **Retry** to re-run the failed task without losing sprint progress.
* **Option B: "Close Project"**
    * **Scenario:** The environment is broken and requires external maintenance (e.g., system restart, PATH update).
    * **Action:** Pauses the sprint safely. Klyve saves the current project state and closes it, allowing you to resume after fixing the environment.

---

## 3. Handling Logic & Test Failures
These occur when generated code fails requirements or breaks an interface.

* **Option A: Retry Automated Fix**
    * **Scenario:** You suspect there's an error that the AI missed. Force one more bugfix cycle.
* **Option B: Pause for Manual Fix (Recommended)**
    * **Scenario:** The logic is complex, or the AI is caught in a loop.
    * **Action:** Launches the **Manual Fix Workflow** (see below).
* **Option C: Skip Task & Log as Bug**
    * **Scenario:** The feature is non-critical.
    * **Action:** Bypasses the task. Klyve marks the feature as **Blocked** and auto-creates a **High-Priority Bug Report** in the backlog.

---

## 4. The "Manual Fix" Workflow
Seamlessly interject your expertise into the automated pipeline.

* **Prerequisite:** A valid **IDE Path** must be configured in *File > Settings*.
* **Step 1:** Click **"Pause for Manual Fix & Investigate"** on the Debug Dashboard.
* **Step 2:** Klyve launches your IDE and opens the relevant files.
* **Step 3:** You debug the code and run tests locally to ensure they pass. Save the file.
* **Step 4:** Return to Klyve and click **"Resume Sprint"**. The system detects your external changes, verifies them, and proceeds.

---

## 5. Handling Regression Failures
At the end of a sprint, Klyve runs mandatory verification tests. Failures here are handled differently depending on whether the *tool* failed or the *code* failed.

### A. Environment Failures (Tooling Issues)
These occur if the test runner fails to execute (e.g., "command not found," missing libraries).

* **Option A: "I have fixed the issue, Retry"**
    * **Action:** Re-attempts to execute the test command after you have corrected the system environment.
* **Option B: "Close Project"**
    * **Action:** Safely pauses the project to allow for external system configuration (e.g., restarts, shell updates). Resuming brings you back to this checkpoint.

### B. Logic Failures (Assertion Errors)
These occur when the tests execute successfully but report failures in your code (failed assertions).

* **Option A: Debug Manually (Pause the Sprint)**
    * **Action:** The sprint remains open. You follow the **Manual Fix Workflow** to resolve the regression (in your IDE if you configured it in Klyve).
* **Option B: Acknowledge & Complete (Ship with Issues)**
    * **Action:** The sprint is marked **Completed** and features are merged.
    * Klyve automatically creates a **High-Priority Bug Report** in the backlog for the regression failure, ensuring technical debt is tracked.