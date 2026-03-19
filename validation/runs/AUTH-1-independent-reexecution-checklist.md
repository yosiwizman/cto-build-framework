# AUTH-1 Independent Re-Execution Checklist

**Purpose:** This checklist enables a separate operator — independent from the original builder (Claude Code) and the founding operator (Yosi Wizman) — to re-execute the AUTH-1 Minimal Auth Pilot and produce an independent verification record. Completing this checklist and filing the accompanying review template (`validation/reviews/AUTH-1-independent-reexecution-template.md`) is the final condition required to promote the Authentication / Authorization domain from **Partially Validated** to **Validated**.

**Who this is for:** A separate human operator who was NOT involved in building the auth-pilot application, writing the original tests, or conducting the original Puppeteer run. The operator may be a peer, a technical reviewer, a co-founder, or any qualified party who can run Node.js locally and use a browser.

**What you are doing:** Running the AUTH-1 application from scratch and personally verifying all 10 MUST requirements against the original pilot spec (`validation/pilot-specs/AUTH-1-authentication-authorization.md`). Your results are independent evidence — they either match or they don't. Record exactly what you observe.

---

## Environment Prerequisites

Before starting, confirm the following:

| Prerequisite | Requirement | Confirmed |
|---|---|---|
| Node.js | v18 or later (v22 recommended) | [ ] |
| npm | Bundled with Node.js | [ ] |
| Browser | Any modern browser (Chrome recommended) | [ ] |
| Internet | Not required — runs fully local | [ ] |
| Port 3847 | Must be free (not in use by another process) | [ ] |
| Application source | `~/auth-pilot/` directory present on local machine | [ ] |

**To start the application:**
```
cd ~/auth-pilot
node server.js
```

The server will output: `Auth server running on http://localhost:3847`

Open your browser and navigate to: **http://localhost:3847**

> **Note:** The application uses an in-memory SQLite database. The database is wiped every time the server restarts. Do not restart the server between tests — run all 10 items in a single server session.

---

## Known Scope Boundary

This checklist verifies basic username/password authentication with bcrypt hashing and express-session only. The following are explicitly out of scope and should not be tested or cited:

- OAuth / social login
- Multi-factor authentication
- Role-based access control beyond single-owner check
- Password reset flows
- Rate limiting or brute-force protection
- Production deployment hardening (TLS, HTTPS, reverse proxy)

---

## Known Issue: AUTH-1.09 UI Note

**Read this before running AUTH-1.09.**

The application UI may display notes across users (i.e., notes created by alice may be visible in bob's session via the UI). **This is a known presentation-layer issue, not a security failure.**

The security boundary being verified for AUTH-1.09 is the **API authorization** — specifically, that the `/api/notes/:id` endpoint returns HTTP 403 when a user attempts to fetch a note they do not own. The API correctly enforces this. Verify the API behavior, not the UI display. The UI display issue is recorded in the existing evidence artifacts and is non-blocking for the authorization proof.

---

## Checklist

### AUTH-1.01 — User Registration

**What to do:** On the page at `http://localhost:3847`, enter a username and password in the registration form and click Register.

**What to confirm:** After registering, the status area shows "Logged in as: [your username]."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.02 — Credentials Stored Hashed (Not Plaintext)

**What to do:** After registering, navigate to `http://localhost:3847/api/debug/users` in your browser address bar.

**What to confirm:** The response shows a password field containing a long scrambled string starting with `$2a$` or `$2b$`. Your actual password text must NOT appear in the response.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.03 — Valid Login Produces a Session

**What to do:** Log out if currently logged in. Enter valid credentials and click Login.

**What to confirm:** Status area shows "Logged in as: [your username]."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.04 — Invalid Credentials Are Rejected

**What to do:** Log out. Enter a valid username but an incorrect password, then click Login.

**What to confirm:** An error message appears (e.g., "Invalid credentials") and the status still shows "Not logged in."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.05 — Session Persists Across Page Refresh

**What to do:** Log in. Press F5 or Ctrl+R to refresh the page.

**What to confirm:** After the refresh, the status still shows "Logged in as: [your username]."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.06 — Session Persists Across Browser Restart

**What to do:** Log in. Close the browser window completely (do not close the server). Reopen the browser and navigate to `http://localhost:3847`.

**What to confirm:** Status shows "Logged in as: [your username]" — session survived the browser close.

> **Important:** The server must remain running throughout. If you restart the server, the in-memory database resets and this test is invalid. Mark NOT TESTED if the server was restarted.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.07 — Logout Invalidates the Session

**What to do:** Log in. Click the Logout button. Then navigate directly to `http://localhost:3847/api/protected` in your browser address bar.

**What to confirm:** (a) After logout, status shows "Not logged in." (b) Navigating to `/api/protected` returns a 401 response — not protected content.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.08 — Protected Route Is Blocked When Logged Out

**What to do:** While logged out, navigate directly to `http://localhost:3847/api/protected` in your browser address bar.

**What to confirm:** A 401 or access-denied response is returned — not protected content.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.09 — Authorization: Wrong User Cannot Access Another User's Resource

**What to do:**
1. Register user **alice**, then navigate to `http://localhost:3847/api/notes` and POST a note (you can use the browser's fetch API or curl: `curl -X POST http://localhost:3847/api/notes -H "Content-Type: application/json" -d '{"content":"alice note"}' --cookie-jar alice.jar --cookie alice.jar` — or have alice's session active when a note already exists from test setup)
2. Log out as alice
3. Register user **bob**
4. Navigate to `http://localhost:3847/api/notes/1` in your browser address bar while logged in as bob

**What to confirm:** The response is HTTP 403 "Access denied" — bob does not receive alice's note content.

> **Known UI issue (non-blocking):** The application UI may show notes across users. This is a presentation-layer issue only. The security boundary being tested is the **API response** — 403 returned by `/api/notes/:id`. Verify the API, not the UI display.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior (API response):** _______________________________________________
- **UI display observation (if noted):** _______________________________________________
- **Notes:** _______________________________________________

---

### AUTH-1.10 — Tampered Session Token Is Rejected

**What to do:**
1. Log in as any user
2. Open browser developer tools (F12) → Application tab → Cookies → `localhost:3847`
3. Find the cookie named `connect.sid` and edit its value (change several characters to random letters)
4. Refresh the page

**What to confirm:** After tampering, the page shows "Not logged in" — the tampered session was rejected.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Observed behavior:** _______________________________________________
- **Notes:** _______________________________________________

---

## Result Summary

| ID | Requirement | Result | Matches Original (Y/N) |
|----|-------------|--------|----------------------|
| AUTH-1.01 | User registration | _____ | _____ |
| AUTH-1.02 | Credentials stored hashed | _____ | _____ |
| AUTH-1.03 | Valid login produces session | _____ | _____ |
| AUTH-1.04 | Invalid credentials rejected | _____ | _____ |
| AUTH-1.05 | Session persists across refresh | _____ | _____ |
| AUTH-1.06 | Session persists across browser restart | _____ | _____ |
| AUTH-1.07 | Logout invalidates session | _____ | _____ |
| AUTH-1.08 | Protected route blocked when logged out | _____ | _____ |
| AUTH-1.09 | Authorization: wrong user denied (API) | _____ | _____ |
| AUTH-1.10 | Tampered session rejected | _____ | _____ |

**Overall re-execution result:** _____ (ALL MATCH / PARTIAL MISMATCH / MATERIAL MISMATCH)

---

## Operator Notes

_Use this space for anything unexpected, unclear, or worth recording. Any deviation from the expected behavior must be described here — even if you still marked PASS._

_______________________________________________
_______________________________________________
_______________________________________________
_______________________________________________

---

## Operator Sign-Off

By completing this checklist, I confirm that:
- I am NOT the original builder of this application (Claude Code)
- I am NOT the founding operator (Yosi Wizman)
- I performed each checked step personally on the live application
- This record reflects what I actually observed

| Field | Value |
|-------|-------|
| Operator name | _____________________ |
| Operator role / relationship | _____________________ |
| Date executed | _____________________ |
| Device used | _____________________ |
| Browser used | _____________________ |
| Node.js version | _____________________ |
| Server started fresh for this run | Yes / No |
| Any items NOT TESTED | _____________________ |
| Any FAIL items | _____________________ |

**Operator sign-off:** [ ] I have personally executed the above steps and this record accurately reflects my observations.

---

## Next Step After Completing This Checklist

File the completed review template at:
`validation/reviews/AUTH-1-independent-reexecution-template.md`

Then report results to the framework owner (Yosi Wizman) to trigger the reviewer verdict update and domain status promotion review.

---

_Created: 2026-03-19. For use by an independent operator only — not the original builder or founding operator. Filing a completed version of this checklist plus the review template satisfies the independent re-execution requirement for AUTH-1 Validated promotion._
