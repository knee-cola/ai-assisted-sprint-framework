# 📑 Sprint Playbook Template
## 0. Sprint Status

```
Status: [🔲 not started | 🚧 in progress | 🛠️ implementing <user story id> | ✅ done]
```
---

## 1. Sprint Metadata

* **Sprint ID:** \[unique identifier]
* **Start Date:** \[YYYY-MM-DD]
* **End Date:** \[YYYY-MM-DD]
* **Sprint Goal:** \[clear and concise goal statement]
* **Team/Agent Responsible:** \[AI agent name/version]
* **Branch Name (Git):** \[feature/sprint-<id>]

---

## 2. Current State of Software

*(Concise snapshot of the project before Sprint work begins)*

* **Main Features Available:** \[list]
* **Known Limitations / Issues:** \[list]
* **Relevant Files / Modules:** \[list with paths]
* **Environment / Dependencies:** \[runtime versions, frameworks, libs]

---

## 3. Desired State of Software

*(Target state after Sprint is complete)*

* **New Features:** \[list]
* **Modified Features:** \[list]
* **Expected Behavior Changes:** \[list]
* **External Dependencies / Integrations:** \[list]

---

## 4. User Stories

Each story represents a **unit of work** that can be developed and tested independently.

| Story ID | Title          | Description                              | Acceptance Criteria          | Definition of Done                               | Assignee    | Status |
| -------- | -------------- | ---------------------------------------- | ---------------------------- | ------------------------------------------------ | ----------- | ------ |
| US-1     | \[short title] | \[detailed description of functionality] | \[conditions for acceptance] | \[implemented, tested, docs updated, lint clean] | \[AI agent] | 🔲  todo |
| US-2     | ...            | ...                                      | ...                          | ...                                              | ...         | 🔲 todo |

**Status options:** `🔲 todo`, `🚧 in progress`, `🚫 blocked`, `✅ done`

---

## 5. Technical Instructions

*(Guidance to help AI converge quickly on the correct solution)*

* **Code Snippets / Patterns:**

  ```python
  # Example placeholder snippet
  def example_function():
      pass
  ```
* **Architecture Guidelines:** \[layering, module boundaries, design patterns]
* **Coding Style Conventions:** \[naming rules, formatting, linting]
* **Testing Strategy:** \[unit/integration, testing framework, coverage target]

---

## 6. Risks and Dependencies

* **Risks:** \[list potential blockers, e.g., API instability, missing test coverage]
* **Dependencies:** \[other modules, external services, libraries, team inputs]

---

## 7. Sprint Definition of Done (DoD)

The Sprint is complete when:

**AI-Responsible Items** (AI agent can verify and tick):
* [ ] All user stories meet their individual Definition of Done.
* [ ] Code compiles and passes automated tests.
* [ ] Code is committed and pushed on branch `[feature/sprint-<id>]`.
* [ ] Documentation is updated.
* [ ] Sprint status updated to `✅ done`.

**User-Only Items** (Only user can verify and tick):
* [ ] Branch is merged into main.

---

