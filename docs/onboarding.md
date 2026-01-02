---
layout: default
title: Project Creation
parent: User Documentation
nav_order: 2
---

# Project Creation
{: .fs-9 }

Starting a new build or resuming a legacy project.
{: .fs-6 .fw-300 }

---

## 1. Creating a New Application
This workflow is for greenfield projects. You provide the intent; Klyve provides the architectural elaboration.

### Step 1: Initialize
* **Navigate:** *File > New Project* and select **"Create from a New Specification"**.
* **Jira Integration (Optional):**
    * Go to *Project Settings > Integrations* to enable two-way backlog sync.
    * Input your **URL**, **Username**, and **Jira API Token** to authenticate.

### Step 2: The Project Brief
You do not need a perfect technical document to start.
* **Text Mode:** Paste a raw description (e.g., *"A Java-based retail inventory system..."*).
* **File Mode:** Upload existing PDF or Word requirements documents. The better the spec the better the final deliverables.
* **Analysis:** Klyve scans the input to identify core features and missing requirements.

### Step 3: Lifecycle Assessment
Before generating specs, Klyve assesses the project type:
* **UX Decision:** It asks if a **UX Specification** is needed. For backend-only component development, it will suggest skipping this.
* **Fast-Track:** For very small or clearly defined scripts, it may recommend skipping the elaboration phase entirely and moving straight to development.

### Step 4: Specification Ratification
Klyve generates the foundational documents for your review.
* **UX/UI Spec:** User personas, journeys, and screen definitions.
* **Application Spec:** Functional requirements and scope.
* **Technical Spec:** Stack selection, database schema, API architecture.
* **Action:** Review the drafts. Use **"Refine"** to request changes, then click **"Approve"** to lock the scope, generate **coding standards**, receive documented guidance for preparing the **dev and test environments**, generate build scripts and generate the project backlog.

---

## 2. Onboarding an Existing Codebase
This workflow is for legacy maintenance. Klyve ingests your local source code to build a context map.

### Step 1: Back up your Codebase
* AI may make mistakes, and this presents a risk that it may silently introduce new errors into your existing codebase or damage it. To mitigate this risk, always make sure you **have a backup of your current codebase** available before you make a change to it using Klyve.

### Step 2: Select Target
* **Navigate:** *File > New Project* and select **"Work with an Existing Codebase"**.
* **Input:** Browse to the root folder of the application in which the user has made the code base files available.

### Step 3: Pre-Flight Scan
Klyve performs a non-destructive read-only scan.
* **Safety:** Verifies valid source code and checks for Git repositories.
* **Indexing:** Builds a "Project Memory," allowing the AI to understand the architecture without re-reading every file for every task.

### Step 4: Reverse-Engineering
Klyve establishes a baseline by generating "Reverse-Engineered" specifications:
* **Baseline Docs:** Creates Application and Technical Specifications that reflect the *current* state of the system.
* **Outcome:** These documents become the source of truth for future changes.

### Step 5: Maintenance Dashboard
Once indexed, you are taken to the Dashboard.
* **Status:** Displays detected languages and codebase health.
* **Next Step:** Define your coding standards, then navigate to the **Project Backlog** to begin adding bug reports or changes. 
* **After a change:** After the successful completion of each fix or change, remember to **back up your code again as a risk mitigation against potential AI mistakes in the next change**.