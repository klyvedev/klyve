---
layout: default
title: Setup & Configuration
parent: User Documentation
nav_order: 1
---

# Setup & Configuration
{: .fs-9 }

Getting the Factory operational on your local machine.
{: .fs-6 .fw-300 }

---

## 1. Installation
Klyve is distributed as a standalone binary. It does not require any local Python environment or dependency management.

### Windows
* **File:** `setup_klyve_v1.0_Beta.exe`
* **Action:** Download and run the installer. It deploys the application and creates a secure local database in your user home path.

### Linux
* **File:** 'Klyve-x86_64.AppImage'
* **Action:**
    1.  Download the file.
    2.  Mark it as executable: `chmod +x Klyve-x86_64.AppImage`
    3.  Run it directly. No installation required.

---

## 2. First-Run Initialization
Upon the first launch, you must accept the **License & Privacy Policy Agreement**.

* **The Legal Guardrail:** This step explicitly confirms your ownership of the output and your consent to transmit code fragments to your chosen LLM provider via API.
* **Action:** Navigate through the "EULA" and "Privacy Policy" tabs to enable the acceptance checkbox.

---

## 3. Connecting Intelligence (LLM Setup)
Klyve follows a **"Bring Your Own Key" (BYOK)** model. You pay your provider directly; Klyve acts as the secure orchestration layer.

1.  Navigate to **File > Settings > LLM Service Configuration**.
2.  **Select Provider:** Choose OpenAI, Anthropic, DeepSeek, Grok, Gemini, local LLM, Other OpenAI-compatible, or a **Custom Endpoint**.
3.  **Enter API Key:** Your key is stored in the local, encrypted database and is never sent to Klyve's servers.

### The "Chain of Thought" Strategy
To optimize costs and performance, you can assign different models to different tasks:

* **Reasoning Model (High Capability):** Used for complex tasks like architectural planning, code generation, and debugging.
* **Quick Model (High Speed):** Used for lower-stakes tasks like summarization, file parsing, and log analysis.

> **Note:** You can assign the Quick Model to both roles to save costs, but code quality may degrade.
{: .note }

---

## 4. Other External Conveniences
Klyve uses a "Sidecar" pattern to minimize dependencies, but a few external integrations have been offered for convenience:

* **Git:** Ensure Git is installed and accessible in your system PATH for version control integration.
* **IDE:** Configure your preferred editor (e.g., `code.cmd`, `pycharm64.exe`) in **File > Settings > IDE Configuration**. This allows Klyve to launch your editor during manual debugging sessions.
* **Templates:** You can upload custom `.docx` styles and templates in **File > Settings > Templates** if you need the generated specs to match a corporate style and structure.

---

## 5. Defining the Factory Floor
Before initiating a project, you must define where Klyve operates. Navigate to **File > Settings > Factory Behavior**.

* **Work Directory:** The root folder where new project repositories will be created (e.g., `D:\Dev\KlyveProjects`). On Linux remember to set access permissions for the path.
* **Archive Directory:** The destination folder for finalized project exports.
* **Max Debug Attempts:** Defines how many times Klyve attempts to self-correct a failure before escalating to you.