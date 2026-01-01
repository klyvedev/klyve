---
layout: page
title: Capabilities
nav_order: 2
permalink: /capabilities/
---

# Capabilities
{: .fs-9 }

Klyve handles the heavy lifting of software engineering, allowing you to focus on architecture and product decisions.
{: .fs-6 .fw-300 }

---

## 1. Specification & Architecture
Most coding assistants require you to think in code snippets. Klyve thinks in projects.
* **Spec Generation:** Describe your feature either in plain English or upload a fuller set of requirements, and Klyve converts it into detailed UX/UI, application and technical specifications.
* **Architecture Management:** Klyve maintains the "big picture" of your project structure, ensuring new features fit into your existing design.

## 2. Automated Development
Once a specification is approved, Klyve acts as your implementation team.
* **Code Generation:** Klyve writes functional, standard code to match the requirements.
* **Refactoring:** It can update existing code to improve structure or performance without breaking functionality.
* **Dependency Management:** Klyve identifies library imports and requirements automatically.

## 3. The Testing Engine
Klyve ensures reliability through a hybrid testing approach.
* **Unit Tests:** Klyve automatically writes **and** runs unit tests for the code it generates.
* **UI Testing:** For visual elements, Klyve generates detailed **manual test cases** that guide you through verifying the user interface.
* **Custom Integration Tests:** Klyve writes backend regression and integration test scripts, and executes them automatically as part of the sprint process.

## 4. Documentation and Reporting
Documentation is treated as a first-class citizen, not an afterthought.
* **Live Docs:** As code changes, Klyve updates and versions the corresponding documentation. You can access all project documentation in the Document Hub, **add review comments and record approvals** for each document.
* **Traceability:** You can trace every requirement forward to implemented functions in a **Requirements Traceability Report**.
* **Reporting:** A Reports Hub provides you with information about project completion, sprint performance and sprint deliverables. Access your sprint histories through the Projects menu.

## 5. Security, Data Sovereignty & Governance
Klyve is architected for professionals who require strict control over their intellectual property.

* **Governance (Human-in-Command):** You retain absolute authority. Klyve requires your specific authorization to proceed with every development task. It cannot execute development tasks without your approval.
* **Encrypted State Storage:** All internal project artifacts (specs, code history, state) are stored in a **secure, encrypted local database**.
* **No Third-Party Leakage:** Your IP is never shared with Klyve.online. It exists only on your encrypted local database, your file system and the LLM provider you explicitly choose.
* **Accessible Outputs:** For your convenience, Klyve automatically mirrors the latest approved versions of your Code, Readme files, and documentation (as .docx, .xlsx, and .md files) to your designated project folder in plain text.

### Supply Chain Security (US EO 14028)
Klyve is built for professional environments that require strict software provenance.
* **Automated SBOM:** Every release includes a cryptographically verifiable **Software Bill of Materials (SPDX JSON)**.
* **Zero-Trust Build:** Our build pipeline (Nuitka + Syft) ensures full transparency of all primary and binary dependencies.

---
[Get Started Now](https://github.com/klyvedev/klyve/releases){: .btn .btn-primary .fs-5 }