# Klyve
**The Automated Software Factory**

> Execute the entire software lifecycle, from requirements to deployment, on your local machine.
> No cloud dependencies. No lost IP.

[![Watch the Klyve Demo](https://img.youtube.com/vi/Pc7RQGKFCoU/maxresdefault.jpg)](https://www.youtube.com/watch?v=Pc7RQGKFCoU "Watch Klyve in Action")
*Click to watch the 40-second tour*

---

### 📥 Download
Klyve is a compiled desktop application.
You can download the latest installer for Windows and AppImage for Linux from the **[Releases Page](https://github.com/klyvedev/klyve/releases)**.

---

### 📸 The Visual Tour

**1. From Idea to Spec**
Don't start from scratch. Upload raw requirements, and Klyve generates your UX/UI, Application, and Technical specifications.
![Analysis Phase](screenshots/01_input.png)

**2. Automated Architecture**
Klyve generates the architecture, build scripts, and Docker containers before writing the code.
![Spec Generation](screenshots/02_specs.png)

**3. Self-Healing Execution**
The "Senior Partner" engine detects build failures and attempts automatic bug fixes in real-time.
![Auto Bug Fix](screenshots/04_auto_fix.png)

**4. Professional Deliverables**
Keep stakeholders happy with auto-generated traceability matrices and sprint reports.
![Reporting](screenshots/06_report.png)

---

### ⚠️ Release Notes & Troubleshooting

**Known Issues (Beta)**
* **Project Reports:** Four specific project reports have not yet been implemented in this release. The menu options for these in the *Reports Hub* will appear disabled.
* During a sprint, the AI sometimes takes a few minutes to generate the unit test scripts, during which time the system idles. Do not close the application. It will resume its work once the scripts are complete. 
* During the initial acceptance of the EULA, Linux users may have to click on the Privacy Policy tab twice for the Policy to be displayed. 
* On the first launch, the app takes several seconds to initialize itself before the EULA appears for acceptance. Subsequent startups will be quicker.
* When the EULA appears for acceptance on first launch of the app, Linux users will need to click twice on the Privacy Policy tab for the policy to be displayed.
  

**Troubleshooting**
* **Linux Users:** If Klyve fails to start after a re-install, you may need to clear the local database state. Run the following command in your terminal:
    ```bash
    rm -rf ~/.klyve
    ```