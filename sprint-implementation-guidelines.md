# 📘 Sprint Implementation Guidelines

These guidelines define how the AI agent must implement a Sprint based on the approved **Sprint Playbook**.
They ensure consistent execution, traceability, and alignment with user expectations.

---

## 0. Key Definitions

**Logical Unit of Work (LUW)**: A single, cohesive code change that:
- Implements one specific functionality 
- Can be described in 1-2 sentences
- Passes all relevant tests
- Can be committed independently

**Blocked Status**: A user story cannot proceed due to:
- Missing external dependencies 
- Conflicting requirements
- Failed tests that cannot be auto-fixed
- Missing user clarification

**AI-Responsible DoD Items**: Checkboxes the AI can verify and tick:
- Code compiles and passes tests
- Code committed and pushed to branch
- Documentation updated
- Sprint status updated to done

**User-Only DoD Items**: Checkboxes only the user can tick:
- Branch merged into main
- Production deployment completed
- External integrations verified

---

## 1. Git & Version Control Rules

### 1.1 Commit Granularity

* Commit after each **logical unit of work (LUW)**.
* A user story may span multiple commits.
* Do not mix unrelated changes (e.g., no “feature + formatting” in one commit).
* Include tests for the LUW in the same commit if the story's DoD requires tests.
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

* Run build and fix issues before committing.
* Commit and push regularly (at least daily).

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
* Update each story’s `Status` field (`🔲 todo` → `🚧 in progress` → `✅ done`).
* Mark `✅ done` only when the story’s **DoD** is fully satisfied.

### 2.2 Sprint Status (Top-Level)

* Keep the top-level Sprint status current:

  ```
  Status: [🔲 not started | 🚧 in progress | 🛠️ implementing <user story id> | ✅ done]
  ```

### 2.3 Commit & Status Sync

**Strict choreography**

- **First commit of a story**  
  Include the first code changes for `US-#` **and** update the Playbook in the same commit:
  - Sprint status → `🛠️ implementing US-#`
  - Story `US-#` status → `🚧 in progress`

- **Final commit of a story**  
  Include the completing code changes for `US-#` **and** update the Playbook in the same commit:
  - Story `US-#` status → `✅ done`
  - Tick any **AI-responsible** DoD items that became true in this commit (see below)

- **DoD checkbox updates**  
  Tick AI-responsible DoD items **in the same commit** that makes them true:
  - ✅ Code compiles and passes automated tests
  - ✅ Code is committed and pushed on branch  
  - ✅ Documentation is updated
  - ✅ Sprint status updated to done
  
  **NEVER tick user-only DoD items** such as:
  - ❌ Branch is merged into main
  - ❌ Production deployment completed
  - ❌ External systems integration verified
  
- **No status-only commits**  
  Avoid standalone “status update” commits. If a previous commit forgot a status/DoD tick, include it in the **very next** code commit for that story.


### 2.4 Location & Traceability

* Store Playbook in repo under `docs/sprints/sprint-<id>.md`.
* Reference Story IDs in commit messages.

### 2.5 End-of-Sprint Update

* Update Sprint status → `✅ done`.
* Update Playbook with final status changes.
* Stop execution.

---

## 3. Coding & Testing Standards

### 3.1 Style Guides

* Follow project’s existing style guides.
* Follow existing style guides exactly unless deviation prevents story completion.
* If deviation is necessary, document rationale in commit body and ask user for approval.
* Do not mix stylistic mass-changes with functional code.

### 3.2 Code Quality

* Keep changes minimal and scoped.
* Favor readability and idiomatic solutions.
* Maintain module boundaries.
* Add/update docstrings and project docs when behavior changes.

### 3.3 Testing Policy

* **Unit tests**: required for all backend logic, utilities, data processing, and business logic.
* **UI tests**: required only if the story's DoD explicitly mentions testing UI behavior.
* Pure styling changes (CSS-only) do not require tests.
* **Integration/E2E tests**: explicitly out of scope.
* Maintain existing test coverage levels.

### 3.4 Test Execution

* Run relevant tests locally before committing.

### 3.5 Prohibited

* No large-scale refactors unless explicitly requested.
* No new frameworks or test harnesses.
* No speculative features.

---

## 4. Execution Flow

### 4.1 Story Execution Workflow

**STEP 1: Start Story**
1. Verify previous story is `✅ done` or `blocked`
2. Change story status from `🔲 todo` to `🚧 in progress`
3. Change sprint status to `🛠️ implementing US-#`
4. Commit these playbook changes with first code changes for the story

**STEP 2: Implement Story (Loop)**
For each LUW in the story:
1. Write code for one logical unit of work
2. Write tests if required by story DoD
3. Run tests and fix any failures
4. Commit LUW with conventional commit message including "Refs: US-#"
5. Push commit to branch

**STEP 3: Complete Story**
1. Verify all story acceptance criteria are met
2. Verify all AI-responsible DoD items are complete
3. Run final test suite 
4. Update story status to `✅ done`
5. Tick completed AI-responsible DoD checkboxes 
6. Commit these playbook updates
7. Push final commit

**STEP 4: Next Story**
- Proceed to STEP 1 for next story
- If no more stories, proceed to End-of-Sprint workflow

### 4.2 End-of-Sprint Workflow

**STEP 1: Final Verification**
1. Verify all stories are `✅ done`
2. Run complete test suite
3. Update any remaining documentation

**STEP 2: Sprint Completion**  
1. Update sprint status to `✅ done`
2. Tick any remaining AI-responsible DoD items
3. Commit final changes
4. Push branch to remote

**STEP 3: Stop Execution**
- Report sprint completion to user
- Do not merge branch or open PRs

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

### 6.1 Error Response Protocol

**MANDATORY STEPS when encountering any blocker:**
1. Stop current work immediately
2. Mark story status as `blocked` in playbook
3. Add specific blocker reason to playbook
4. Commit playbook changes
5. Ask user for explicit resolution 
6. Wait for user response - do not proceed

### 6.2 Specific Error Actions

**Test Failures:**
1. Run tests again to confirm failure
2. Copy exact error messages
3. Mark story as `blocked` with reason: "Tests failing: [error summary]"
4. Ask user: "Tests are failing with error: [exact error]. Should I fix this or wait for guidance?"

**Missing Dependencies:**
1. Identify exactly what is missing
2. Mark story as `blocked` with reason: "Missing dependency: [name]"
3. Ask user: "Missing dependency [name]. Should I install it or mock it for testing?"

**Conflicting Requirements:**
1. Document the specific conflict
2. Mark story as `blocked` with reason: "Conflicting requirements: [details]"  
3. Ask user: "Found conflicting requirements: [details]. Which approach should I follow?"

**Build/Compilation Failures:**
1. Copy exact build error
2. Mark story as `blocked` with reason: "Build failing: [error summary]"
3. Ask user: "Build is failing with: [exact error]. How should I resolve this?"

### 6.3 Prohibited Actions During Blocking

**NEVER do these when blocked:**
- Continue to next story
- Make speculative fixes
- Change requirements to work around issues
- Skip failing tests
- Implement workarounds without approval

### 6.4 Unblocking Requirements

**AI can only resume work after user provides:**
- Explicit instruction on how to resolve the blocker
- Modified requirements if applicable  
- Confirmation that workaround approach is acceptable

---

## 7. Sprint Wrap-Up

### 7.1 Completion Criteria

Sprint is complete when:

* All user stories = `✅ done`.
* Sprint status = `✅ done`.
* Final status updates completed.
* Code committed to Sprint branch.
* Docs and comments updated.
* Tests passing (when applicable).

### 7.2 Handover

* AI stops execution.
* Sprint branch remains unmerged.

### 7.3 Final Note

* No changes beyond Sprint scope.
* Playbook + Git history act as audit record.
