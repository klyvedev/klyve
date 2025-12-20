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
The **Project Backlog** (Epic > Feature > User Story) is the single source of truth.

### Impact Analysis (Pre-Sprint Check)
Before scheduling an item, Klyve must assess risk.
1.  Regular items for fresh development are to be selected as *To Do* items and added into the sprint. 
2. If it is a *Change Request* or *Bug Report* item, click **"Run Impact Analysis"** first. Klyve scans the codebase and generates a **Technical Preview**, listing exactly which files will be modified or read. For Bug Reports, a root cause hypothesis is formed. 
3.  **Stale Prevention:** If you use Git, Klyve checks timestamps. If code has changed since the last analysis (e.g., a merge occurred), the item is marked "Stale" and must be re-analyzed afresh before planning.

---

## 2. Sprint Planning
Bundle analyzed items into a sprint.

### Plan Generation
* **Action:** Click **"Plan Sprint"**.
* **Outcome:** Klyve generates a sequential **Implementation Plan** (the technical roadmap).
* **Auditing:** You can optionally run an AI Audit (Security, Scalability, or Best Practice) against the proposed plan.

### Approval
You must **Approve** the plan. If the architecture looks wrong, reject it here to force a replan. Code is never written without an authorized plan.

---

## 3. The Execution Phase
The interface shifts to the **Live Log**. Klyve iterates through the plan task-by-task:

1.  **Logic Synthesis:** Converts requirements into a pseudocode strategy.
2.  **Code Generation:** Writes source code adhering to your **Coding Standards**.
3.  **Auto-Review:** Scans for syntax errors and style violations.
4.  **Unit Testing:** Generates and runs a unit test for the specific component.
5.  **Commit:** Saves work to the local repository.

> **Handling Failures:** If a task fails, Klyve attempts to self-correct (up to your *Max Debug Attempts*). If it fails, you can **"Pause for Manual Fix"**, launch your IDE, fix the code, and click **"Resume"**.
{: .note }

---

## 4. The Quality Gates
Once coding is complete, Klyve enforces three strict gates.

### Gate 1: Backend Regression
* **Action:** Klyve runs the full backend test suite (consisting of your command or tool to run all the unit test scripts that Klyve generated already).
* **Failure:** You must either debug manually or **"Acknowledge & Log"** (which completes the sprint but auto-creates a High-Priority Bug in the backlog).

### Gate 2: Temporary Integration Test
Klyve writes and runs a new transient script (e.g., `sprint_integration_temp.py`) to verify that the *new* modules in the sprint interact correctly. 
* **Action:** You can review, edit, or execute this generated test command. 

### Gate 3: Context-Aware UI Testing
(Only for GUI Projects)
* **Option A: Automated UI Test:** Writes and executes scripts with your configured runner (Selenium, Playwright, etc.).
* **Option B: Manual Test Plan:** Klyve generates a human-readable **Manual Test Checklist**. You download it, perform the verification manually, and mark the gate as passed.

---

## 5. Closure
* **Documentation Sync:** Klyve automatically updates the Application and Technical Specifications to reflect the changes made during the sprint.
* **Release:** The sprint is marked *Completed*. You can now close the project or return to the backlog.