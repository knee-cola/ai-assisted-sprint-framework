# 🏗️ AI-Assisted Sprint Framework

This framework lets a human user and an AI agent run software development sprints in a **structured, auditable, and predictable** way.

- The **human** defines goals and reviews plans.  
- The **AI agent** generates a detailed Sprint **Playbook** and implements it step by step.  
- The **user** keeps final control over scope and **merging**.

---

## 📑 Files Overview

- **sprint-playbook-template.md** – Markdown structure for defining a Sprint.  
- **how-to-use-sprint-playbook-template.md** – AI-facing guide for generating Playbooks.  
- **sprint-implementation-guidelines.md** – AI-facing rules for execution.  
- **sprint-implementation-quick-reference.md** – One-page checklist for execution.  
- **sprint-playbook-example.md** – Example Playbook (formatting illustration only).  

---

## 🎯 Motivation

Without structure, AI coding agents can:
- Drift from the intended goal  
- Make speculative changes  
- Leave work hard to track/audit

This framework adds **Agile-style discipline**:
- The **Sprint Playbook** = a contract between human and AI  
- The **Guidelines** = strict execution rules  
- The **User** = always in control of merges and scope

---

## 🚀 How to Use

⚠️ **Important**: Before asking the AI to generate or execute a Sprint, always tell it to **read the framework files**:  
- `sprint-playbook-template.md`  
- `how-to-use-sprint-playbook-template.md`  
- `sprint-implementation-guidelines.md`  
- `sprint-implementation-quick-reference.md`  

This ensures the AI is aligned with the framework rules and structure.

---

### Step 1 — Define the Sprint Goal
Tell the AI what you want at a high level.

**Prompt example**
```

I want this Sprint to add user authentication to my task management app.
Users should be able to register, log in, and log out.

```

---

### Step 2 — Generate the Sprint Playbook
Ask the AI to **read the template + how-to guide** before generating the Playbook.  
It should ask clarifying questions until scope is clear.  
(Guardrail: examples are for formatting only—don’t copy their tech choices.)

**Prompt example**
```

Read the following files before proceeding:

* sprint-playbook-template.md
* how-to-use-sprint-playbook-template.md

Now, create a Sprint Playbook for the goal I just described.
If anything is ambiguous or contradictory, ask me questions
until the scope is clear. Keep the plan minimal and focused.

```

**Revision example**
```

Update the Sprint Playbook:

* Drop logout for now.
* Require password hashing with bcrypt.
* Keep endpoints versioned under /api/v1.

```

---

### Step 3 — Approve the Playbook
Review the generated Playbook:
- Is the **Sprint Goal** accurate?
- Are **User Stories** minimal and testable?
- Do **Technical Instructions** match your stack?

When satisfied, approve it.

**Prompt example**
```

The Playbook looks good. Approved.
Proceed to execution using the Sprint Implementation Guidelines.

```

---

### Step 4 — Execute the Sprint
Ask the AI to **read the guidelines + quick reference + the approved Playbook** before starting.  
It will then:
- Work sequentially through user stories  
- Commit after each logical unit of work (LUW)  
- Update the Playbook (Markdown) in the same commit  
- Stop when Sprint is complete  
- ❌ Not merge or open PRs (user merges)

**Prompt example**
```

Read the following files before proceeding:

* sprint-implementation-guidelines.md
* sprint-implementation-quick-reference.md
* docs/sprints/sprint-08-auth.md   # (the approved Playbook for this Sprint)

Follow the Sprint Implementation Guidelines strictly.
Commit after each logical unit of work and update the Playbook status
in the same commit. Stop when the Sprint is marked done.

```

**If the AI gets stuck** (test failures, missing deps, contradictions), it must **stop and ask you**.

**Prompt example (when blocked)**
```

You’ve hit a blocker? Show me the exact error and where it occurs.
Do not proceed until I respond.

```

---

### Step 5 — Review & Merge
When the AI marks the Sprint as **done**:
- Inspect the Sprint branch and commits  
- Verify the updated Playbook  
- If satisfied, **you merge** the branch into `main`

**Prompt example (final check)**
```

Show me the final Sprint Playbook and the list of commits you created,
in order, with their messages.

```

---

## ✅ Benefits

- **Clarity** — Clear goals and structure for the AI  
- **Traceability** — Playbook + commits = full audit trail  
- **Safety** — AI cannot merge or expand scope without approval  
- **Simplicity** — Markdown + Git; no extra tools needed

---

## 📌 Notes

- Keep Playbooks in `docs/sprints/` for history.  
- The AI **must not** merge or open PRs.  
- Extend this framework with your project’s conventions (linting, CI rules, DoD checklists).  
