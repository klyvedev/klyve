---
layout: default
title: How It Works
nav_order: 3
---

# The Workflow
{: .fs-9 }

A chronological look at the "Factory Floor" - from raw idea to built release.
{: .fs-6 .fw-300 }

---

## Step 1: The Input (Elaboration)
**The Goal:** Move from "vague idea" to "ratified specification" without the friction of a blank page.

You start by opening the **New Project Dialog**. You have two choices:
1.  **New Application:** You paste a raw text brief (or upload .docx or PDF spec documents).
2.  **Existing Codebase:** You point Klyve to a local directory to index your current architecture.

Klyve's **Analysis Engine** scans your input. It doesn't just "read" it; it assesses it to figure out the best project lifecycle path forward and (if it's a new application) also advise you of its own confidence of being able to complete it - in a documented report.*

Once ambiguities are resolved, Klyve generates a professional **Application Specification** and **Technical Specification**. You review these documents online. You can edit them directly, or ask Klyve to refine any part of them. Nothing is finalized until you click **"Approve."** You can also record your client's approval or anything else you want to note in a Document Management area.

---

## Step 2: The Logic (Planning)
**The Goal:** Translate the "What" (Specs) into the "How" (Work Items) before writing code.

Once the specs are approved, Klyve generates a hierarchical **Project Backlog** of Epics and Features. You select the items you want to tackle in the upcoming sprint.

Before the sprint starts, two critical checks occur:
1.  **Impact Analysis:** Klyve determines which existing files will be touched by the new features, flagging potential regressions and blocking execution if it finds unfulfilled dependencies.
2.  **Implementation Planning:** The system generates a step-by-step **Logic Plan**. It details exactly which functions will be created, which classes will be refactored, and the order of operations.

**The Checkpoint:** You read the plan. If Klyve proposes an architectural pattern you dislike, you reject the plan and provide feedback. **Code is never written without a plan you have authorized.**

---

## Step 3: The Execution (The Implementation Pipeline)
**The Goal:** Automated, serialized production of high-quality code.

You click **"Start Sprint."** The interface shifts to the **Live Log View**. You are no longer typing; you are supervising the development. Klyve iterates through the plan task-by-task:

1.  **Logic Generation:** It converts the task requirements into a pseudocode logic plan.
2.  **Code Generation:** It writes the actual source code, strictly adhering to your project's **Coding Standards**.
3.  **Automated Review:** A separate agent reviews the generated code for syntax errors and style violations.
4.  **Unit Testing:** It generates and runs unit tests immediately for the new component.
5.  **Commit:** If all tests pass, the code is committed to your local Git repository.

**Handling Errors:**
If a test fails or an API breaks, Klyve attempts to self-correct, if you configured it to do so. If it cannot, the pipeline pauses and the issue is escalated to you. You can choose to **"Pause for Manual Fix,"** which launches your local IDE (e.g., VS Code or any other) with the relevant files open. You fix the bug, save the file, and Klyve resumes the pipeline, progressing through integration testing and UI testing.

---

## Step 4: The Delivery (Review & Release)
**The Goal:** A clean handoff of working software and updated documentation.

When the sprint tasks are complete, Klyve runs the **Full Regression Suite** to ensure no previous features were broken.

Upon success, you receive:
1.  **The Code:** Committed, merged, and ready for deployment.
2.  **The Reports:** A full Backlog Traceability Report and Test Execution Report.
3.  **The Documentation:** Your Application and Technical Specifications are automatically updated to reflect the changes made during the sprint, ensuring your docs never rot.


You are now ready to deploy—or select the next set of features and start the cycle again.
