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

**MANDATORY PROCESS:**
1. **STOP playbook creation immediately**
2. **Ask user for specific clarification** with concrete questions:
   * *"Do you want authentication for all users or just admins?"*
   * *"Should performance improvements target backend response times or frontend rendering?"*
   * *"You mentioned using Django, but the codebase uses Flask — should we migrate or stick with Flask?"*
3. **Wait for user response** - do not proceed with assumptions
4. **Repeat clarification cycle** until goal is completely unambiguous
5. **Only then proceed** to create the playbook

**CRITICAL RULE**: Never proceed with unclear requirements - this will cause blocking during implementation.

---

### 2. Assess Current State

**MANDATORY STEPS:**
1. Read project entry points (e.g., `main.py`, `index.js`, `app.py`)
2. Identify and read core business logic modules
3. Read configuration files (`.env`, `config.*`, etc.)
4. Read dependency files (`package.json`, `requirements.txt`, `Cargo.toml`, etc.)
5. List current main features available
6. List known limitations or issues
7. List relevant file paths
8. Document runtime versions, frameworks, and libraries

**Output Requirements:**
* Keep descriptions factual and concise (2-3 sentences per item)
* Focus only on functionality relevant to the sprint goal
* Do not speculate about future capabilities

---

### 3. Sprint ID Selection (Mandatory Process)

**EXACT STEPS TO FOLLOW:**
1. **Check if `docs/sprints/` directory exists**
   - If directory doesn't exist: set **Sprint ID = `01`**
   - If directory exists: proceed to step 2

2. **List existing sprint files**
   - Search for files matching pattern: `docs/sprints/sprint-??-*.md`
   - Extract only the two-digit numbers (ignore everything else)
   - Example: `sprint-03-auth.md` → extract `03`

3. **Calculate new ID**
   - If no matching files found: set **Sprint ID = `01`**
   - If files found: find maximum ID number and increment by 1
   - Preserve zero-padding (e.g., `03` → `04`, `09` → `10`)

**CRITICAL RULES:**
- NEVER use IDs from example documents - examples are for formatting only
- NEVER guess or assume sprint IDs
- ALWAYS preserve two-digit zero-padding format
- This is the single source of truth for Sprint ID assignment

---

### 4. Define Desired State

**MANDATORY SECTIONS:**
1. **New Features** - List exactly what new functionality will be added
2. **Modified Features** - List existing features that will be changed
3. **Expected Behavior Changes** - Describe how user/system behavior will differ
4. **External Dependencies/Integrations** - List new libraries, APIs, or services needed

**Requirements:**
* Each item must be specific and measurable
* Avoid vague terms like "improve" or "enhance" - be precise
* Only include changes directly needed for the sprint goal

---

### 5. Break Down Into User Stories

**STORY CREATION RULES:**
1. Each story must be implementable independently
2. Story should require 1-2 commits maximum
3. Story must have measurable acceptance criteria
4. Story must include specific DoD items

**MANDATORY STORY COMPONENTS:**
* **Story ID**: Sequential numbering (`US-1`, `US-2`, `US-3`...)
* **Title**: 2-4 word description of the functionality
* **Description**: Clear explanation of what needs to be implemented
* **Acceptance Criteria**: Specific, testable conditions that must be met
* **Definition of Done**: Concrete checklist (implemented, tested, docs updated, lint clean)
* **Assignee**: Always `AI-Agent` for AI-implemented sprints
* **Status**: Always starts as `🔲 todo`

**STATUS PROGRESSION (AI must follow exactly):**
* `🔲 todo` → `🚧 in progress` → `✅ done`
* If blocked: any status → `🚫 blocked` (requires user intervention)
* **CRITICAL**: If ANY story becomes `🚫 blocked`, STOP all sprint work immediately

---

### 6. Add Technical Instructions

**REQUIRED SECTIONS:**
* **Code Snippets/Patterns**: Include specific code examples that show structure
* **Architecture Guidelines**: Define module boundaries, layering, design patterns
* **Coding Style Conventions**: Specify naming rules, formatting, linting requirements
* **Testing Strategy**: Define what testing is required (unit/integration, framework, coverage)

**GUIDELINES:**
* Provide concrete examples, not abstract descriptions
* If multiple approaches exist, specify exactly which one to use
* Include specific commands for building, testing, and linting
* Reference existing project conventions where possible

---

### 7. Capture Risks and Dependencies

* List potential **risks** (technical, integration, scope-related).
* List **dependencies** (modules, libraries, APIs, data sources).

---

### 8. Apply Definition of Done (DoD)

**USER STORY DoD (for each story):**
* Must include specific, measurable items like:
  * "Endpoint implemented and returns correct status codes"
  * "Unit tests added with 80%+ coverage"
  * "Documentation updated in README"
  * "Code passes linter without errors"

**SPRINT DoD STRUCTURE (mandatory separation):**

**AI-Responsible Items** (AI MUST tick these when completed):
* [ ] All user stories meet their individual Definition of Done
* [ ] Code compiles and passes automated tests
* [ ] Code is committed and pushed on branch `[feature/sprint-<id>]`
* [ ] Documentation is updated
* [ ] Sprint status updated to `✅ done`

**User-Only Items** (AI MUST NEVER tick these):
* [ ] Branch is merged into main
* [ ] Production deployment completed (if applicable)
* [ ] External system integrations verified (if applicable)

**CRITICAL RULE**: AI agents must NEVER tick user-only DoD items under any circumstances.

---

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

## ✅ Output Requirements

**MANDATORY CHECKLIST** - Sprint Playbook must have:

1. ✅ **Correct Sprint ID** - Follow Sprint ID selection rule (increment from existing)
2. ✅ **Complete metadata** - All fields in Sprint Metadata section filled
3. ✅ **Current state analysis** - Based on actual project file examination
4. ✅ **Specific desired state** - Measurable outcomes, not vague goals
5. ✅ **Independent user stories** - Each story can be implemented separately
6. ✅ **Testable acceptance criteria** - Each story has specific pass/fail conditions
7. ✅ **Concrete DoD items** - Specific, actionable checklist items
8. ✅ **Technical guidance** - Actual code snippets and specific instructions
9. ✅ **Risk identification** - Potential blockers and dependencies listed
10. ✅ **Proper DoD separation** - AI vs User responsibilities clearly marked

**VALIDATION**: Before finalizing, verify that another AI agent could execute the sprint based solely on the playbook content without additional clarification.