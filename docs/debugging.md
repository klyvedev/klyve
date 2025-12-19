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
Klyve acknowledges that code generation is probabilistic and environments are brittle. It does not crash when a development task fails; it enters a **Triage State**.

### Self-Correction
Before bothering you, the system attempts to fix the error automatically.
* **Logic:** It analyzes the stack trace and the failed test output.
* **Action:** It refactors the code or adjusts the test case.
* **Persistence:** It repeats this process up to the number of times defined in your **Max Debug Attempts** setting (*File > Settings*).

If the error persists beyond these attempts, the pipeline pauses and escalates the decision to you via the **Debug Dashboard**.

---

## 2. Handling Environment Failures
These occur when the factory floor is missing a tool (e.g., `npm` not found, `pytest` command invalid, network timeout).

**The Decision Point:**
* **Option A: "I have fixed the issue, Retry"**
    * **Use Case:** You forgot to install a dependency or your internet dropped.
    * **Action:** Fix the external issue (e.g., `pip install x`) in your terminal. Click **Retry** to re-run the failed task without losing sprint progress.
* **Option B: "Stop & Export Project"**
    * **Use Case:** The environment is hopelessly broken.
    * **Action:** Aborts the sprint safely and tells you what was wrong. Klyve saves the current state of the project, allowing you to resume after you have fixed the environment.

---

## 3. Handling Logic & Test Failures
These occur when the generated code fails to meet requirements or breaks an existing interface.

**The Decision Point:**
* **Option A: Retry Automated Fix**
    * **Use Case:** You see an obvious syntax error in the log that the AI missed.
    * **Action:** Force the system to try one more generation cycle.
* **Option B: Pause for Manual Fix (Recommended)**
    * **Use Case:** The logic is complex, or the AI is caught in a loop. You know exactly how to fix it in 30 seconds.
    * **Action:** Launches the **Manual Fix Workflow** (detailed below).
* **Option C: Skip Task & Log as Bug**
    * **Use Case:** The feature is non-critical, and you want to finish the rest of the sprint.
    * **Action:** Bypasses the task. Klyve marks the parent feature as **Blocked** and automatically creates a **High-Priority Bug Report** in the backlog containing the failure logs.

---

## 4. The "Manual Fix" Workflow
This feature allows you to seamlessly interject your expertise into the automated pipeline.

* **Prerequisite:** A valid **IDE Executable Path** must be configured in *File > Settings*.
* **Action:** Click **"Pause for Manual Fix & Investigate"** on the Debug Dashboard.
* **System Behavior:**
    1.  Klyve pauses the sprint.
    2.  It launches your IDE (e.g., VS Code, PyCharm, or whatever you configured) and automatically opens the specific files involved in the stack trace.
* **User Step:**
    1.  Debug the code using your standard tools.
    2.  Run the test locally to ensure it passes.
    3.  Save the file.
* **Recovery:** Return to Klyve and click **"Resume Sprint"**. The system detects the file change, re-runs the verification step, and proceeds to the next task if successful.

---

## 5. Handling Regression Failures
At the end of a sprint, Klyve runs the full **Backend Regression Suite**. If a previous feature breaks, you have a strategic choice:

### Option A: Debug Manually (Stop the Line)
* **Action:** Choose the manual debug option.
* **Outcome:** The sprint remains open. You follow the Manual Fix workflow to resolve the regression before the sprint can be marked as complete.

### Option B: Acknowledge & Complete (Ship with Issues)
* **Action:** Choose **"Acknowledge Failures & Complete Sprint"**.
* **Outcome:**
    1.  The sprint is marked as **Completed**.
    2.  The new features are merged.
    3.  Klyve automatically creates a **Bug Report** in the backlog for the regression failure, ensuring technical debt is tracked rather than ignored.