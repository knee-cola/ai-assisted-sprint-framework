# 📘 How to Use the Sprint Playbook Template

*(Guide for AI Agent)*

---

## 🎯 Purpose

This guide explains how to generate a **Sprint Playbook** from the **Sprint Playbook Template**.
The Playbook is the **authoritative plan and tracking file** for the Sprint.
Your role as AI agent is to:

1. Interpret the user’s Sprint goal.
2. Analyze the current project state.
3. Split work into clear user stories.
4. Populate the Playbook with concise, actionable details.
5. Ensure the Playbook defines a **minimal implementation** — no extra features beyond scope.

---

## 🛠 Step-by-Step Instructions

### 1. Analyze User Input

* Read the user’s description of what should be achieved in the Sprint.
* Extract the **general goal** (e.g., “add authentication,” “improve reporting,” “fix performance issues”).
* Note any explicit **constraints** (frameworks, coding styles, patterns).

**If gaps, ambiguities, or contradictions are detected:**

* Ask the user for clarification.
* Examples of clarifications:

  * *“Do you want authentication for all users or just admins?”*
  * *“Should performance improvements target backend response times or frontend rendering?”*
  * *“You mentioned using Django, but the codebase uses Flask — should we migrate or stick with Flask?”*
* Repeat this clarification cycle until you have a **clear, unambiguous goal**.

---

### 2. Assess Current State

* Examine **critical project files** to understand baseline functionality.

  * Entry points (e.g., `main.py`, `index.js`).
  * Core business logic modules.
  * Configuration files.
  * Dependency files (`package.json`, `requirements.txt`).
* Summarize current capabilities, limitations, and dependencies.
* Keep the description **short and factual**.

---

### 3. Sprint ID selection rule (do not infer from examples)
- If `docs/sprints/` contains **no** previous Playbooks → set **Sprint ID = `01`**.
- Otherwise:
  1) List files matching `docs/sprints/sprint-??-*.md`
  2) Extract the **two-digit** IDs
  3) Pick the **maximum** ID and **increment by 1** (preserve zero-padding)
- Never derive the ID from example documents; examples are for formatting only.

---

### 4. Define Desired State

* Translate user goal into **target outcomes**:

  * New features.
  * Modified features.
  * Expected behavior changes.
* Mention any **external dependencies** (libraries, APIs).
* Be concise and specific.

---

### 5. Break Down Into User Stories

* Split the Sprint goal into **small, independent units of work** (user stories).
* Each story must:

  * Have a unique ID (`US-1`, `US-2`, ...).
  * Contain a short title + clear description.
  * Have **acceptance criteria** (conditions that must be met).
  * Include a **Definition of Done** (code implemented, tested, docs updated).
* Keep stories small enough to fit into 1–2 commits each.

---

### 6. Add Technical Instructions

* Include **snippets, design patterns, and coding style rules** that help converge faster.
* Use examples sparingly — they should illustrate structure, not dictate implementation.
* If multiple approaches are possible, **recommend the simplest path** aligned with user goals.

---

### 7. Capture Risks and Dependencies

* List potential **risks** (technical, integration, scope-related).
* List **dependencies** (modules, libraries, APIs, data sources).

---

### 8. Apply Definition of Done (DoD)

* Attach a DoD to each **user story**.
* Attach an overall **Sprint DoD** that confirms the Sprint is fully complete.
* Ensure DoDs cover:

  * Implementation.
  * Testing.
  * Documentation.
  * Branch/commit flow.

---

### 9. Metrics (Optional)

* Estimate story points (if applicable).
* Add a placeholder for velocity tracking.

---

## ⚠️ Guardrail Against Overfitting

If you are provided with **example Sprint Playbooks**:

* Use them **only to understand formatting and structure**.
* Do **not** copy their technologies, libraries, or domain-specific details unless explicitly relevant.
* Always prioritize:

  1. **Sprint Playbook Template**
  2. **User instructions**
  3. **Project state analysis**

---

## ✅ Output

At the end of this process, produce a **complete Sprint Playbook** that:

* Follows the template structure exactly.
* Is concise, consistent, and minimal.
* Can guide execution without ambiguity.