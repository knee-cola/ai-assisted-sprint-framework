# 📝 Sprint Implementation Quick Reference

## 1. Git Rules

* Branch: `feature/sprint-<id>-<goal>` (from `main`)
* Commits: one per **logical unit of work (LUW)**
* Commit style: **Conventional Commits** + `Refs: US-#`
* Push regularly; run linters/tests before committing
* ❌ Do not merge or open PR — user merges

---

## 2. Playbook Updates

* Update **User Story status**: `🔲 todo` → `🚧 in progress` → `✅ done`
* Update **Sprint status** at top of Playbook:

  ```
  [🔲 not started | 🚧 in progress | 🛠️ implementing <user story id> | 📝 documenting | ✅ done]
  ```
* Status changes **committed with code changes**
* Playbook lives in `docs/sprints/sprint-<id>.md`
- **First story commit:** set Sprint → `implementing US-#` and story → `🚧 in progress` (same commit as first code).
- **Final story commit:** set story → `✅ done` and tick any AI-owned DoD items that became true (same commit).

---

## 3. Coding & Testing

* Follow existing style guides; light deviations only if better outcome
* Unit tests when appropriate (backend logic, utilities, etc.)
* UI-only changes may omit tests
* ❌ No integration/E2E tests
* No large-scale refactors or new frameworks

---

## 4. Execution Flow

* Work **sequentially** through stories
* LUWs → commits, update Playbook in same commit
* Mark story `done` only when DoD is met
* Don’t start next story unless current is `done` or `blocked`
* At end: `documenting` → finalize → `done` → stop

---

## 5. Documentation

* Update inline code comments (new/changed funcs/classes)
* Update README/API docs/configs if behavior changes
* Docs updated **in same commit** as related code
* ❌ No Sprint summary reports

---

## 6. Failures

* If blocked: **stop + ask user**
* ❌ No auto-fixes, no speculative changes
* May mark Playbook story as `blocked` with note

---

## 7. Wrap-Up

* All stories = `✅ done`
* Sprint status = `✅ done`
* Final status updates completed
* Branch ready, tests/docs complete
* AI stops — user merges

