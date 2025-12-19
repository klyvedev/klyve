---
layout: default
title: Setup & Configuration
parent: User Documentation
nav_order: 1
---

# Setup & Configuration
{: .fs-9 }

Getting the Factory Floor operational on your local machine.
{: .fs-6 .fw-300 }

---

## 1. Installation
Klyve is distributed as a compiled, standalone installer for Windows or an AppImage executable for Linux. It does not require any local environment or dependency management.

### Windows
* **Artifact:** `setup_klyve_v1.0_Beta.exe`
* **Method:** Standard Windows Installer.
* **Action:** Run the installer. It will deploy the application to the path of your choice, create a secure local database in your user home path, and register the uninstaller.

### Linux
* **Artifact:** `klyve.bin` (AppImage)
* **Method:** Portable Executable.
* **Action:**
    1.  Download the file.
    2.  Mark it as executable (if not already done).
    3.  Run it directly. No installation required.

---

## 2. First-Run Initialization
Upon the first launch, Klyve initializes itself.

### The Legal Guardrail
Before the main interface loads, you must accept the **License & Privacy Policy Agreement**.
* **Purpose:** Klyve is a tool that processes your intellectual property. This step explicitly confirms your ownership of the output and your consent to transmit code fragments to your chosen LLM provider via API.
* **Action:** Navigate through both, the "EULA" and "Privacy Policy" tabs to enable the acceptance checkbox.
* **Revocation:** You may revoke this consent at any time via *File > Settings > Factory Behavior > Reset License & Permissions*, which will wipe your local credentials and terminate the application.

---

## 3. Connecting Intelligence (LLM Setup)
Klyve follows a **"Bring Your Own Key" (BYOK)** model. You pay your provider directly; Klyve acts as the secure orchestration layer.

### Configuration Steps
1.  Navigate to **File > Settings**.
2.  Select the **LLM Service Configuration** tab.
3.  Choose your provider (e.g., OpenAI, Anthropic, DeepSeek, or a Custom Endpoint). 
4.  Enter your **API Key**. Keys are stored continuously in the local, encrypted database. There are no Klyve servers, so your keys are never sent anywhere except to your selected LLM provider, who requests them in order to authenticate your registration with them.

### The "Chain of Thought" Strategy
To optimize costs and performance, Klyve allows you to assign different models from your selected provider to different tasks within the same project.
* **Reasoning Model (High Capability):** Used for complex tasks like architectural planning, code generation, and debugging. 
* **Quick Model (High Speed):** Used for lower-stakes tasks like summarization, file parsing, and log analysis.
If you want to reduce costs further you can assign the quick model for both, reasoning as well as quick tasks, but there may be a trade-off in the quality of output. 

---

## 4. Environment Dependencies
Klyve uses a "Sidecar" deployment pattern to minimize external dependencies.

* **Git:** Klyve integrates with your local Git executable for version control. Ensure Git is installed and accessible in your system PATH if you want Klyve to use it.
* **IDE:** Klyve can launch your preferred editor during debugging sessions. Configure the path to your executable (e.g., `code.cmd`, `pycharm64.exe`) in *File > Settings > IDE Configuration*.
* **Document Styles and Templates (Optional):**
    * **Purpose:** Ensures that all generated specification documents (UX Spec, Application Spec, Tech Spec) adhere to the document specification structures and visual format of your choice. Klyve uses its own default template and styling if you don't wish to provide yours.
    * **Configuration:** Navigate to *File > Settings > Templates* to upload your preferred templates for specification documents. Navigate to *File > Settings > Docx Styles* and upload a `.docx` file containing your defined styles (headers, fonts, margins) to set it as the **Active Style**.
* **Automated Debugging Limit:**
    * **Purpose:** Controls the "persistence" of the AI. Defines how many times Klyve attempts to self-correct a logic or test failure before pausing and escalating the decision to you.
    * **Configuration:** Navigate to *File > Settings* (General or Factory Behavior) and set the **Max Debug Attempts** value.

---

## 5. Project Workspace Configuration
Before initiating your first project, you must define the local filesystem paths where Klyve is authorized to operate.

### Defining the Factory Floor
Navigate to *File > Settings > Factory Behavior* to configure these mandatory paths.

* **Work Directory (Default Base Path):**
    * **Action:** Set the root folder **including the drive letter in Windows)** where all new project repositories will be created (e.g., `D:\Dev\KlyveProjects`). The drive letter is not required on Linux, but you must have permissions for the path you enter.
    * **Note:** Klyve will create individual subdirectories for each project within this path.
* **Archive Directory (Export Path):**
    * **Action:** Set the destination folder for finalized project exports (archives). 
    * **Behavior:** When you select "Export Project" from the File menu, the system will compress the project state and save the artifact here for long-term storage.