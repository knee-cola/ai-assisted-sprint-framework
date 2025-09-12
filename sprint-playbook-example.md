## ⚠️ Instruction to AI Agent

This is an **example Sprint Playbook**.

* Use it **only** to understand the **structure, formatting, and level of detail** required when filling in a Sprint Playbook Template.
* **Do not** copy the example’s technologies, libraries, coding styles, or domain-specific details unless they are explicitly relevant to the current Sprint you are generating.
* Always prioritize the **Sprint Playbook Template** and the **user’s instructions** over anything in this example.

---

## 0. Sprint Status

```
Status: not started
```

---

## 1. Sprint Metadata

* **Sprint ID:** Sprint-07
* **Start Date:** 2025-09-15
* **End Date:** 2025-09-29
* **Sprint Goal:** Implement user authentication (login/logout) using JWT tokens.
* **Team/Agent Responsible:** AI-Agent-v1.2
* **Branch Name (Git):** feature/sprint-07-authentication
* **Capacity Estimate:** 20 story points

---

## 2. Current State of Software

* **Main Features Available:**

  * Task CRUD operations (create, update, delete).
  * Project organization with categories.
  * Basic UI for task lists.

* **Known Limitations / Issues:**

  * No user authentication.
  * API endpoints are all public.
  * No persistent session management.

* **Relevant Files / Modules:**

  * `backend/app.py` (Flask entry point)
  * `backend/routes/tasks.py` (task endpoints)
  * `frontend/src/App.js` (main React entry)

* **Environment / Dependencies:**

  * Backend: Python 3.11, Flask 3.0, SQLite
  * Frontend: React 18, Vite
  * No authentication libraries installed

---

## 3. Desired State of Software

* **New Features:**

  * User registration and login endpoints.
  * JWT token issuance and verification.
  * Logout endpoint (token blacklist).

* **Modified Features:**

  * Protect task-related endpoints → require authentication.
  * Update frontend to support login/logout forms.

* **Expected Behavior Changes:**

  * Only logged-in users can manage tasks.
  * Non-authenticated requests return `401 Unauthorized`.

* **External Dependencies / Integrations:**

  * Add Python `PyJWT` package.
  * Add React `axios` interceptor for JWT tokens.

---

## 4. User Stories

| Story ID | Title                | Description                                               | Acceptance Criteria                                                  | Definition of Done                                       | Assignee | Status |
| -------- | -------------------- | --------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------- | -------- | ------ |
| US-1     | User Registration    | Implement `/register` API to create users.                | Sending POST `/register` with username+password creates user in DB.  | Endpoint implemented, password hashed, unit tests added. | AI-Agent | todo   |
| US-2     | User Login           | Implement `/login` API to issue JWT token.                | Sending POST `/login` returns JWT token when credentials are valid.  | Endpoint implemented, tests added, token expires in 1h.  | AI-Agent | todo   |
| US-3     | JWT Middleware       | Add backend middleware to verify JWT on protected routes. | Protected endpoints return 401 if JWT is invalid or missing.         | Middleware added, all tests passing.                     | AI-Agent | todo   |
| US-4     | Frontend Login Form  | Add login form in React UI.                               | User can log in, token is stored in localStorage.                    | Component implemented, manual test successful.           | AI-Agent | todo   |
| US-5     | Logout Functionality | Implement logout button + backend blacklist.              | Clicking logout clears token and backend rejects blacklisted tokens. | Code implemented, unit + integration tests added.        | AI-Agent | todo   |

---

## 5. Technical Instructions

* **Code Snippets / Patterns:**

  ```python
  # Example JWT token generation
  import jwt, datetime
  SECRET_KEY = "change_me"

  def create_token(user_id: int):
      payload = {
          "user_id": user_id,
          "exp": datetime.datetime.utcnow() + datetime.timedelta(hours=1)
      }
      return jwt.encode(payload, SECRET_KEY, algorithm="HS256")
  ```

* **Architecture Guidelines:**

  * Keep authentication routes in `backend/routes/auth.py`.
  * Middleware goes into `backend/middleware/jwt.py`.

* **Coding Style Conventions:**

  * Backend: PEP8.
  * Frontend: ESLint + Prettier.

* **Testing Strategy:**

  * Backend: Pytest unit tests for auth endpoints.
  * Frontend: Cypress integration test for login flow.
  * Coverage target: ≥ 80%.

---

## 6. Risks and Dependencies

* **Risks:**

  * Incorrect JWT handling may block all endpoints.
  * Token storage in frontend may be vulnerable if mishandled.

* **Dependencies:**

  * `PyJWT` for backend.
  * `axios` interceptor in frontend.

---

## 7. Sprint Definition of Done (DoD)

The Sprint is complete when:

* [ ] All user stories meet their individual DoD.
* [ ] Code compiles and passes automated tests.
* [ ] Feature branch `feature/sprint-07-authentication` pushed to remote.
* [ ] Branch merged into `main`.
* [ ] Documentation (`README.md`) updated with authentication usage.
* [ ] Sprint status updated to **done**.

---

## 8. Metrics / Tracking (Optional)

* **Planned Story Points:** 20
* **Completed Story Points:** TBD
* **Velocity Trend:** Last Sprint delivered 18 SP.
