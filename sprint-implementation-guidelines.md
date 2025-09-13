# 📘 Sprint Implementation Guidelines

These guidelines define how the AI agent must implement a Sprint based on the approved **Sprint Playbook**.
They ensure consistent execution, traceability, and alignment with user expectations.

---

## 1. Git & Version Control Rules

### 1.1 Commit Granularity

* Commit after each **logical unit of work (LUW)**.
* A user story may span multiple commits.
* Do not mix unrelated changes (e.g., no “feature + formatting” in one commit).
* Include tests for the LUW in the same commit when feasible.
* Local WIP commits may be squashed before delivery, but history must remain clear.

### 1.2 Commit Message Style

* Use **Conventional Commits** format:

  ```
  <type>(<scope>): <subject>

  <body>

  Refs: <Story-ID(s)>
  ```
* Example:

  ```
  feat(auth): add JWT middleware

  Introduces HS256 verification for protected routes.
  Returns 401 for missing/invalid/expired tokens.

  Refs: US-3
  ```
* Allowed `<type>`: `feat`, `fix`, `refactor`, `perf`, `test`, `docs`, `build`, `ci`, `style`, `chore`, `revert`.

### 1.3 Branching Strategy

* Use **one dedicated branch per Sprint**:

  * Naming: `feature/sprint-<id>-<short-goal>`
  * Example: `feature/sprint-07-auth`
* Branch created from `main` and kept up to date via rebase or merge.
* `main` remains protected.

**Sprint ID source of truth:** The Sprint ID **must** follow the “Sprint ID selection rule” in the How-to guide.  
If no prior Playbooks exist in `docs/sprints/`, start at `01`; otherwise increment the greatest existing two-digit ID (keep zero-padding).

### 1.4 Commit & Push Policy

* Run **linters/tests** before committing.
* Commit and push regularly (at least daily).
* Signed commits if required by repository settings.

### 1.5 PR / Merge Rules

* The AI agent **must not merge or open PRs**.
* The AI’s responsibility ends with:

  * Implementing all user stories.
  * Committing changes to the Sprint branch.
  * Ensuring the branch passes all tests.
* The **user merges** the Sprint branch into `main`.

---

## 2. Playbook Status Updating

### 2.1 User Stories

* Update each story’s `Status` field (`todo` → `in progress` → `done`).
* Mark `done` only when the story’s **DoD** is fully satisfied.

### 2.2 Sprint Status (Top-Level)

* Keep the top-level Sprint status current:

  ```
  Status: [🔲 not started | 🚧 in progress | 🛠️ implementing <user story id> | 📝 documenting | ✅ done]
  ```

### 2.3 Commit & Status Sync

**Strict choreography**

- **First commit of a story**  
  Include the first code changes for `US-#` **and** update the Playbook in the same commit:
  - Sprint status → `implementing US-#`
  - Story `US-#` status → `in progress`

- **Final commit of a story**  
  Include the completing code changes for `US-#` **and** update the Playbook in the same commit:
  - Story `US-#` status → `done`
  - Tick any **AI-responsible** DoD items that became true in this commit (see below)

- **DoD checkbox updates**  
  Tick AI-owned DoD items **in the same commit** that makes them true (e.g., tests now pass, docs updated, sprint status set to `done`, branch pushed).  
  The “Branch merged into main” checkbox is **USER-only** — the AI must **never** tick it.

- **No status-only commits**  
  Avoid standalone “status update” commits. If a previous commit forgot a status/DoD tick, include it in the **very next** code commit for that story.


### 2.4 Location & Traceability

* Store Playbook in repo under `docs/sprints/sprint-<id>.md`.
* Reference Story IDs in commit messages.

### 2.5 End-of-Sprint Update

* Update Sprint status → `done`.
* Update Playbook with final status changes.
* Stop execution.

---

## 3. Coding & Testing Standards

### 3.1 Style Guides

* Follow project’s existing style guides.
* **Light deviations allowed** only when they produce a materially better outcome.
* Document rationale for deviations in commit body.
* Do not mix stylistic mass-changes with functional code.

### 3.2 Code Quality

* Keep changes minimal and scoped.
* Favor readability and idiomatic solutions.
* Maintain module boundaries.
* Add/update docstrings and project docs when behavior changes.

### 3.3 Testing Policy

* **Unit tests**: required when appropriate (backend logic, utilities, reducers, etc.).
* UI-only changes may omit tests if not meaningful.
* **Integration/E2E tests**: explicitly out of scope.
* Maintain existing test coverage levels.

### 3.4 Test Execution

* Run relevant tests locally before committing.
* Ensure CI remains green; note unrelated failures as risks.

### 3.5 Prohibited

* No large-scale refactors unless explicitly requested.
* No new frameworks or test harnesses.
* No speculative features.

---

## 4. Execution Flow

### 4.1 Story Order

* Work **sequentially** through stories in Playbook order.
* Skip only if blocked; mark as `blocked` in Playbook, then continue.

### 4.2 Within a Story

* Implement in **LUWs**, each committed separately.
* Update Playbook status in same commit.

### 4.3 Completion

* Mark story `done` only when DoD is met.

### 4.4 Sequential Integrity

* Do not begin next story until current is `done` or `blocked`.

### 4.5 End-of-Sprint

* After final story: update status → `documenting`, finalize docs/tests, then → `done`.
* Stop execution; user handles merge.

---

## 5. Documentation & Communication

### 5.1 Inline Comments

* Update/add comments for new or changed functions/classes/modules.
* Keep concise and technical.

### 5.2 Project Docs

* Update README/API docs/configs when public-facing behavior changes.
* Docs updated in **same commit** as related code.

### 5.3 Exclusions

* No separate Sprint summary reports.
* No speculative documentation outside scope.

---

## 6. Failure & Error Handling

### 6.1 General Rule

* If blocked, **stop and ask user** for clarification.
* Do not attempt auto-fixes or speculative changes.

### 6.2 Examples

* **Test Failures**: stop, show error, ask user.
* **Missing Dependencies**: stop, ask user whether to install/mock.
* **Conflicting Requirements**: stop, ask user to resolve.

### 6.3 Logging

* May mark a story as `blocked` in Playbook with a short note.
* Must not continue to other stories until resolved.

### 6.4 No Autonomous Workarounds

* No speculative changes.
* Always wait for explicit user instruction.

---

## 7. Sprint Wrap-Up

### 7.1 Completion Criteria

Sprint is complete when:

* All user stories = `done`.
* Sprint status = `done`.
* Final status updates completed.
* Code committed to Sprint branch.
* Docs and comments updated.
* Tests passing (when applicable).

### 7.2 Handover

* AI stops execution.
* Sprint branch remains unmerged.
* User reviews and merges branch into `main`.

### 7.3 Final Note

* No changes beyond Sprint scope.
* Playbook + Git history act as audit record.
