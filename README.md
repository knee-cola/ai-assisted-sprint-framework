# 🏗️ AI-Assisted Sprint Framework

This repository contains a framework for running **AI-assisted software development sprints** in a structured, auditable, and predictable way.  

It is designed to let a human user and an AI agent collaborate safely:
- The **human** defines the goals and reviews plans.  
- The **AI agent** generates a detailed Sprint Playbook and executes it step by step.  
- The **user retains final control** over merging and scope decisions.  

---

## 📑 Files Overview

### 1. Sprint Playbook Template
- A **Markdown template** that defines the structure of a Sprint Playbook.  
- Contains fields for: sprint goal, current state, desired state, user stories, technical instructions, risks, and Definition of Done.  
- Purpose: acts as the **blueprint** for every sprint.  

### 2. How to Use the Sprint Playbook Template
- A **guide for the AI agent** explaining how to transform user instructions into a concrete Sprint Playbook.  
- Covers:  
  - How to clarify ambiguous goals with the user.  
  - How to analyze the codebase.  
  - How to break down work into user stories.  
  - How to keep the Playbook minimal, focused, and accurate.  

### 3. Sprint Implementation Guidelines
- Rules the AI agent must follow when executing a Sprint Playbook.  
- Defines:  
  - Git & commit conventions.  
  - How to update the Sprint Playbook as work progresses.  
  - Coding & testing standards.  
  - Execution flow (sequential, LUWs).  
  - Documentation rules.  
  - Failure & error handling (stop and ask the user).  
  - Wrap-up conditions (AI stops, user merges).  
- Includes a **one-page Quick Reference** for fast use.  

---

## 🎯 Motivation

AI coding agents can write code, but without **structure and guardrails** they:  
- Drift from the intended goal.  
- Make speculative changes.  
- Produce work that is hard to track or audit.  

This framework solves that by introducing **Agile-style discipline**:  
- The **Sprint Playbook** = a contract between human and AI.  
- The **Guidelines** = strict rules for execution.  
- The **User** = always in control of scope and final merges.  

---

## 🚀 How to Use

1. **Define Sprint Goal**  
   - The human user describes what should be achieved in the Sprint.  

2. **Generate Sprint Playbook**  
   - The AI agent uses the **Playbook Template** + **How-to Guide** to create a Sprint Playbook.  
   - The user reviews and approves (or edits) it.  

3. **Execute Sprint**  
   - The AI agent follows the **Sprint Implementation Guidelines** to implement the Playbook:  
     - Sequentially through user stories.  
     - Committing after each logical unit of work.  
     - Updating the Playbook as progress is made.  
   - The AI stops when Sprint status = `done`.  

4. **Review & Merge**  
   - The user reviews the Sprint branch.  
   - If satisfied, the user merges it into `main`.  

---

## ✅ Benefits

- **Clarity** → AI knows exactly what to do.  
- **Traceability** → Playbook + commits = complete audit trail.  
- **Safety** → AI cannot merge or change scope without approval.  
- **Simplicity** → Everything is Markdown + Git, no extra tools needed.  

---

## 📌 Notes

- This framework is meant to evolve. Teams may extend it with:  
  - Checklists for specific technologies.  
  - More detailed Definitions of Done.  
  - Project-specific coding standards.  
- By default, it favors **minimalism and safety** over automation.  
