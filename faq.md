---
layout: default
title: FAQ
nav_order: 6
---

# Frequently Asked Questions
{: .fs-9 }

Strategic answers regarding Security, IP, and Factory Logic.
{: .fs-6 .fw-300 }

---

## 1. Security & Intellectual Property

**Q: Does Klyve train on my code?**

**A:** No, Klyve does not train on your code. It handles your specs and code but does not study them or manipulate them. Klyve runs locally on your machine and saves the specs and source code received from the LLM to your disk, and also in a local, encrypted database. It also sends specs and code snippets to the LLM provider you select (e.g., OpenAI, Anthropic) during every project solely for the purpose of executing the next project task, subject to the API privacy policies of that provider. 

**Q: Can I use Klyve offline?**

**A:** Klyve's internal logic, file management, and local database work completely offline. However, the core generative and development capabilities require an internet connection to reach your LLM provider's API.

---

## 2. Technical Control & Quality

**Q: What prevents Klyve from generating unmaintainable "spaghetti code"?**

**A:** Unlike chat interfaces that generate code in a vacuum, Klyve is **State-Aware**.
1.  **Standards:** It strictly adheres to the *Coding Standard* document generated for your specific project.
2.  **Review:** Every block of generated code passes through up to two rounds of automated syntax and style reviews before being committed.
3.  **Context:** It locally retains the context of what it does to ensure new functions align with existing architectural patterns and components already implemented.

**Q: What happens when the AI produces hallucinates or misses details when generating output?**

**A:** Klyve is designed with a "Human-in-the-Loop" architecture. After generating specs, you get to review and ask for edits, or even edit the specs yourself. You can also decide how many attempts the AI should make to fix a bug. If the AI cannot solve a debugging problem within this limit, or a test fails, the system pauses and escalates to you. You can launch the **Manual Fix** workflow to open the code in your IDE, fix the logic, and resume the sprint. You are always the ultimate authority.


**Q: I want to make a change to an approved spec document before I begin my development. Can I jump back to that step?**

**A:** No. You can't jump back and redo a document that's already been approved. You can only modify it while it's still in the draft stage (pre-approval). Down the line, once created a backlog you can edit a backlog item that hasn't been implemented yet, or you can raise a new change request for implementation, which ends with a spec document update. 

---

## 3. Operations & Cost

**Q: Is there a monthly subscription?**

**A:** No. The Klyve executable is free to download and use. Klyve follows a **"Bring Your Own Key" (BYOK)** model. You pay your preferred LLM provider directly for API usage. This gives you complete control over your operational costs and model choices.

**Q: Which LLM models are supported?**

**A:** Klyve supports major providers including OpenAI (GPT-4o), Anthropic (Claude 3.5 Sonnet), and others that follow the OpenAI API standard. You can also connect with a locally-installed LLM (like Microsoft Phi-3) or connect to an internal LLM hosted on a private cloud (such as a corporate one). You can additionally configure separate models for "Reasoning" (Planning/Coding) and "Quick Tasks" (Summarization) in *File > Settings* to optimize costs.

---

## 4. Factory Logic (How Klyve Thinks)

**Q: How does Klyve determine the implementation plan for a sprint?**

**A:** Klyve reads your selected Backlog Items and cross-references them with your *Technical Specification* and existing codebase. It uses a planning algorithm to determine the most logical sequence of changes (e.g., *Database Schema $\rightarrow$ Backend Logic $\rightarrow$ API Layer*) to minimize dependencies and conflicts.

**Q: How does Klyve know if my specification is ambiguous?**

**A:** Before writing code, the AI scans your requirements for missing parameters, missing details, or contradictory logic. Instead of guessing, it triggers a **Clarification Loop**, flagging the specific gap for your review.

**Q: What should I do if a Regression Test fails at the end of a sprint?**

**A:** You have two strategic options:
1.  **Immediate Fix:** Pause the pipeline, debug the issue manually in your IDE, and retry the test to achieve a clean sprint.
2.  **Acknowledge & Deferred Fix:** If the failure is minor, you can choose to "Acknowledge Failures." Klyve will complete the sprint, deploy the working features, and automatically log a high-priority **Bug Report** in the backlog for the regression.

**Q: How do I handle "State Drift" if I changed code outside of Klyve?**

**A:** When you load a project, Klyve performs a **Pre-flight Check**. If it detects uncommitted external changes, it asks you to confirm them. If you fixed a bug manually between sprints, you can commit those changes during this check to ensure Klyve's understanding of the code state remains in sync with the file system. This option is only available if you run your Klyve project with Git. 
