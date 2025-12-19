---
layout: default
title: The Sprint Cycle
parent: User Documentation
nav_order: 3
---

# The Sprint Cycle
{: .fs-9 }

From Backlog management to the final Quality Gate.
{: .fs-6 .fw-300 }

---

## 1. Backlog Management
The **Project Backlog** is the single source of truth for all work. It is hierarchically structured (Epic > Feature > User Story).

### Adding Work Items
* **Navigation:** *Project > Project Backlog* or use the *Vertical Action Bar > Add New Item*.
* **Action:** Define the item type (Feature, Bug, etc.) and description.
* **Traceability:** Items added here are listed in the end-to-end traceability reports.

### The Impact Analysis (Pre-Sprint Check)
Before a change request item can be scheduled, Klyve must understand its risk profile.
* **Action:** Select a *To Do* item and click **"Run Impact Analysis"**.
* **System Behavior:** Klyve scans the codebase to identify dependencies. It generates a **Technical Preview** listing exactly which files will be modified or read, allowing you to catch conflicts before planning begins.

---

## 2. Sprint Planning
Once items are analyzed, you bundle them into a Sprint by right-clicking each one to select (or remove) it.

### Stale Analysis Prevention
* **The Guardrail:** If you are using Git, Klyve checks the timestamp of the last Impact Analysis of change request items against the latest commit.
* **Behavior:** If the code has changed since the analysis (e.g., a merge occurred), Klyve marks the item as "Stale" and prevents inclusion until re-analyzed. This ensures you never plan against outdated assumptions.

### Plan Generation & Approval
* **Action:** Click **"Plan Sprint"**.
* **Outcome:** Klyve generates a unified **Implementation Plan**. This is a sequential technical development roadmap for the sprint items.
* **User Control:** You must review and **Approve** this plan. If the architecture looks wrong, reject it here to force a replan. You may also use one of the expert AI auditors to get a security audit, scalability audit or a general best practice audit of the logic planned to be implemented in the sprint.

---

## 3. The Execution Phase
Upon approval, the factory enters the **Execution Phase**. The interface shifts to the **Live Log**.

### The Task Loop
Klyve iterates through the approved plan task-by-task:
1.  **Logic Synthesis:** Converts requirements into a pseudocode strategy.
2.  **Code Generation:** Writes source code adhering to your **Coding Standards**.
3.  **Auto-Review:** Scans for syntax errors and style violations.
4.  **Unit Testing:** Generates and runs a unit test for the specific component.
5.  **Commit:** Saves the work to the local repository.

### Handling Failures (The Branching Path)
If a task fails (e.g., a unit test fails or an API call errors):
* **Auto-Triage:** Klyve attempts to self-correct (up to your configured *Max Debug Attempts*).
* **Escalation:** If it remains stuck, it pauses and offers a **Manual Fix** option.
    * **Action:** Click **"Pause for Manual Fix"**. Klyve launches your configured IDE.
    * **Recovery:** Fix the code, save the file, and click **"Resume"** in Klyve. The system detects your external changes and continues the pipeline.

---

## 4. The Quality Gates (Post-Code Verification)
Once all tasks are coded, Klyve enforces a strict, multi-stage Quality Gate before the sprint can be closed.

### Gate 1: Mandatory Backend Regression
* **Action:** Klyve runs the full backend test suite using the command defined in *Project Settings*.
* **Failure Behavior:** You can either pause to debug or **"Acknowledge & Log"** (which completes the sprint but auto-creates a High-Priority Bug in the backlog).

### Gate 2: Temporary Sprint Integration Test
Klyve generates a transient test specifically for the *new* code written in this sprint.
* **System Behavior:** It writes a temporary script (e.g., `sprint_integration_temp.py`) targeting the interaction between the new modules.
* **The Checkpoint:** You are presented with the generated test command.
    * **Run Test:** Executes the temporary script.
    * **Edit Command:** Allows you to modify parameters before running.
    * **Skip:** Bypasses this gate (logged in the sprint report).

### Gate 3: Context-Aware UI Testing
If your project is flagged as a **GUI Project**, a final decision page appears.
* **Option A: Automated UI Test:** Executes your configured UI test runner (e.g., Selenium, Pytest-Qt, etc.). (You must create test scripts. Klyve runs them).
* **Option B: Generate Manual Test Plan:**
    * **Behavior:** Klyve analyzes the UX Spec and generates a human-readable **Manual Test Checklist (Markdown)**.
    * **Outcome:** You download the checklist, perform the manual verification, and mark the gate as passed when you have completed your testing and fixing.

---

## 5. Sprint Review & Closure
* **Documentation Sync:** Upon closure, Klyve automatically updates the **Application Specification** and **Technical Specification** documents to reflect the changes made during the sprint.
* **Release:** The sprint status is updated to *Completed*, and the cycle resets. The system takes you back to the backlog screen where you can start a new sprint. Once you have finished implementing the backlog you can either close and archive the project, and import it again anytime you wish to add new backlog items for implementation.