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
This workflow is for projects starting from scratch. You provide the intent; Klyve provides the architectural elaboration.

### Step 1: Initialize the Project
* **Navigation:** *File > New Project...*
* **Action:** Select **"Create from a New Specification"**.
* **Input:** Enter a Project Name and select a root directory for your new workspace.
* **Jira Integration:**
    * **Purpose:** Enables optional two-way synchronization of backlog items, allowing Klyve to push/pull tickets from your existing Jira board.
    * **Configuration:** Navigate to *Projects > Project Settings > Integrations*. Enter your **URL**, **Username**, and **API Token** to authenticate the connection.


### Step 2: The Project Brief
You do not need a perfect technical document to start. You need a clear intent.
* **Input Method:** You will be presented with the *Specification Elaboration* screen.
    * **Text Mode:** Paste a raw text description of your idea (e.g., "A Python-based inventory management system with a React frontend...").  
    * **File Mode:** Upload existing PDF or Word document(s) containing your requirements. The more you specify the better the results.
* **System Action:** Klyve analyzes the brief to identify core features, missing requirements, and potential technical risks.

### Step 3: The UX and Project Lifecycle Clarification Decisions
Before generating formal application specifications, Klyve asks if you want a full UX spec generated, unless it is very clear your application doesn't need one. For very small applications it may even suggest that you proceed directly to development without going through the specification generation or elaboration phase.
* **The Assessment:** The system will provide you with its assessment and let you decide what you want to do. If what you want is a backend component with very clear specs it may suggest that you skip the elaboration and tech spec phases and go straight to development.

### Step 4: Specification Ratification
Klyve generates two or three foundational documents based on your input. You must review and approve them before any code is written.
* **UX/UI Specification:** Defines Screens and UI styling, User Personas and key User Journeys.
* **Application Specification:** Defines *what* we are building (User Personas, User Journeys, Functional Requirements).
* **Technical Specification:** Defines *how* we are building it (Tech Stack, Database Schema, API Architecture, design patterns).
* **Action:** Review the drafts on the screen. Use the "Refine" button to prescribe or request changes. Click **"Approve"** to lock the scope and proceed towards the Project Backlog, while creating coding standards, dev and test environments, build scripts and dockerfiles along the way.

---

## 2. Onboarding an Existing Codebase
This workflow is for legacy application maintenance projects. Klyve ingests your local source code to build a context map, allowing you to specify changes and execute sprints against an application you didn't write.

### Step 1: Select the Target
* **Navigation:** *File > New Project...*
* **Action:** Select **"Work with an Existing Codebase"**.
* **Input:** Browse to the root folder of the existing application.

### Step 2: The Pre-Flight Scan
Klyve performs a non-destructive read-only scan of the directory.
* **Safety Check:** The system verifies that the directory contains valid source code and checks for existing Git repositories.
* **Indexing:** Klyve builds a detailed understanding of the codebase. This allows the AI to understand work with it without needing to re-read every file for every task.

### Step 3: Reverse-Engineering Specs
To manage the project effectively, Klyve needs a starting baseline.
* **System Action:** Klyve prepared a **Baseline Application Specification** and **Technical Specification**, and also a **UX/UI Specification** and **DB Schema Specification** when applicable.
* **Outcome:** You receive a set of "Reverse-Engineered" documents that describe your current system. These serve as the source of truth for future changes.

### Step 4: The Maintenance Dashboard
Once indexing is complete, you are taken to the **Project Dashboard**.
* **Status:** The system displays the languages detected, the number of files indexed, and the health of the codebase.  
* **Next Step:** Klyve will then help you decide the coding standards it must use. You can then navigate to *Project > Project Backlog* to begin adding Bug Reports or Change Requests against your existing code.