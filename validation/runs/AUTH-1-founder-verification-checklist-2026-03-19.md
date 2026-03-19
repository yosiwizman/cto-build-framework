# AUTH-1 Founder Verification Checklist

**Purpose:** This checklist records the founder's personal manual verification of the AUTH-1 pilot application. The pilot spec (`validation/pilot-specs/AUTH-1-authentication-authorization.md`) requires that Yosi Wizman personally verify the full registration → login → session → logout → denial cycle and sign off on each MUST requirement individually. Puppeteer automation was used during the original build run — it does not satisfy this requirement. This checklist is the mechanism for satisfying it.

**What you are verifying:** A running Node.js + Express application built during the AUTH-1 pilot. It lives outside the repo at `~/auth-pilot/` on your local machine.

**Before you start:**
1. Navigate to `~/auth-pilot/` in your terminal
2. Start the server: `node server.js`
3. Open your browser and go to: `http://localhost:3847`
4. Keep this checklist open alongside the browser

---

## How to Fill This In

For each item:
- Change `[ ]` to `[x]` when you have personally confirmed it
- Set the result field to `PASS`, `FAIL`, or `NOT TESTED`
- Add a note if anything looked unexpected

---

## Checklist

### AUTH-1.01 — User Registration

**What to do:** On the page at `http://localhost:3847`, enter a username and password in the registration form and click Register.

**What to confirm:** After registering, the status area on the page shows "Logged in as: [your username]."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.02 — Credentials Stored Hashed (Not Plaintext)

**What to do:** After registering, navigate to `http://localhost:3847/api/debug/users` in your browser.

**What to confirm:** The password shown is a long scrambled string starting with `$2a$` or `$2b$` — NOT your actual password in readable form.

- [ ] I personally checked the debug endpoint and confirmed the hash format
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.03 — Valid Login Produces a Session

**What to do:** Log out first (click Logout if logged in). Then enter valid credentials and click Login.

**What to confirm:** The status area shows "Logged in as: [your username]."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.04 — Invalid Credentials Are Rejected

**What to do:** Log out. Enter a correct username but a wrong password and click Login.

**What to confirm:** An error message appears (e.g., "Invalid credentials") and the status still shows "Not logged in."

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.05 — Session Persists Across Page Refresh

**What to do:** Log in successfully. Then press F5 or Ctrl+R to refresh the page.

**What to confirm:** After the refresh, the status still shows "Logged in as: [your username]" — you were not logged out by the refresh.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.06 — Session Persists Across Browser Restart

**What to do:** Log in. Close the browser window completely. Reopen the browser and go back to `http://localhost:3847`.

**What to confirm:** The status still shows "Logged in as: [your username]" — the session survived the browser close.

> **Note:** This requires the server to have remained running while you closed and reopened the browser. If you restarted the server, the in-memory database resets and this test is not valid.

- [ ] I performed this step personally (or marked NOT TESTED with reason below)
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.07 — Logout Invalidates the Session

**What to do:** Log in. Click the Logout button. Then try to access `http://localhost:3847/api/protected` directly in your browser address bar.

**What to confirm:** (a) After logout, the status shows "Not logged in." (b) The `/api/protected` URL returns a 401 error or denial message — not your protected data.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.08 — Protected Route Is Blocked When Logged Out

**What to do:** While logged out (or after logout), navigate directly to `http://localhost:3847/api/protected` in your browser address bar.

**What to confirm:** You receive a 401 or access-denied response — you are not shown protected content.

- [ ] I performed this step personally
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.09 — Authorization: Wrong User Cannot Access Another User's Resource

**What to do:**
1. Register user **alice** and create a note (the app has a notes feature used in the automated tests; if you can't access it from the UI directly, this item may require developer assistance to verify manually)
2. Log out
3. Register user **bob** and try to fetch alice's note by navigating to `http://localhost:3847/api/notes/1`

**What to confirm:** Bob receives a 403 "Access denied" response — not alice's note content.

> **Note:** If you cannot reproduce this step manually without developer help, mark NOT TESTED and explain why. The automated test did prove this behavior; your manual verification strengthens the claim but partial verification is recorded honestly.

- [ ] I performed this step personally (or marked NOT TESTED with reason below)
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

### AUTH-1.10 — Tampered Session Token Is Rejected

**What to do:**
1. Log in normally
2. Open your browser's developer tools (F12), go to the Application or Storage tab, find the Cookies section for `localhost:3847`, and find the cookie named `connect.sid`
3. Edit the cookie value — change a few characters in the middle of it to random letters
4. Refresh the page

**What to confirm:** The page now shows "Not logged in" — your tampered session was rejected.

> **Note:** If editing cookies directly is not comfortable, mark NOT TESTED and explain why. The automated test did prove this behavior.

- [ ] I performed this step personally (or marked NOT TESTED with reason below)
- **Result:** _____ (PASS / FAIL / NOT TESTED)
- **Notes:** _______________________________________________

---

## Summary

| ID | Requirement | Result |
|----|-------------|--------|
| AUTH-1.01 | User registration | _____ |
| AUTH-1.02 | Credentials stored hashed | _____ |
| AUTH-1.03 | Valid login produces session | _____ |
| AUTH-1.04 | Invalid credentials rejected | _____ |
| AUTH-1.05 | Session persists across refresh | _____ |
| AUTH-1.06 | Session persists across browser restart | _____ |
| AUTH-1.07 | Logout invalidates session | _____ |
| AUTH-1.08 | Protected route blocked when logged out | _____ |
| AUTH-1.09 | Authorization: wrong user denied | _____ |
| AUTH-1.10 | Tampered session rejected | _____ |

**Overall founder verification result:** _____ (ALL PASS / PARTIAL — see notes / NOT COMPLETED)

---

## Founder Notes

_Use this space for anything unexpected, unclear, or worth recording._

_______________________________________________
_______________________________________________
_______________________________________________

---

## Founder Sign-Off

By completing this checklist, I confirm that I personally operated the live application and verified the items marked above.

- **Founder name:** Yosi Wizman
- **Date verified:** _____________________
- **Device used:** _____________________ (e.g., "MacBook Pro M2, Chrome 123")
- **Server started:** Yes / No
- **Any items NOT TESTED:** _____ (list IDs or "None")
- **Any FAIL items:** _____ (list IDs or "None")

**Founder sign-off:** [ ] I have personally verified the items above and this record is accurate.

---

_Created: 2026-03-19. This checklist is for founder personal verification only. It does not constitute an independent re-execution. When completed, report results to Claude Code to trigger the evidence packet patch and status update._
