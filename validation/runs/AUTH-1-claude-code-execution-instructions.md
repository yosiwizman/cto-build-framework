# AUTH-1 Validation Run — Claude Code Execution Instructions

**AUDIENCE:** Claude Code running on a local Mac Mini M4
**DATE:** 2026-03-18
**REPO:** https://github.com/yosiwizman/cto-build-framework

---

## WHAT THIS IS

This is a complete, self-contained execution plan for the first real domain validation run in the CTO Build Framework. You are executing AUTH-1 — Authentication / Authorization.

The pilot spec is at: `validation/pilot-specs/AUTH-1-authentication-authorization.md`
Read it before starting. It defines the 10 MUST requirements you must prove.

---

## CONSTRAINTS

- Stay STRICTLY inside AUTH-1 scope — no OAuth, MFA, or advanced RBAC
- Every MUST requirement must be verified by Puppeteer browser automation with screenshots
- No manual or assumed verification — if there is no screenshot, it is NOT PROVEN
- All artifacts must be filed in the repo using the existing template structure
- No proof claims may be widened beyond what this run demonstrates
- This is Artifact Class 3 — New Execution Artifact

---

## PHASE 1 — BUILD THE AUTH SYSTEM

Create a temporary project directory (NOT inside the framework repo — use a separate folder like `~/auth-pilot/`).

Build a minimal Node.js + Express application with:

**Dependencies:** express, express-session, better-sqlite3, bcryptjs, puppeteer

**Server (server.js):**
- SQLite database with `users` table (id, username, password_hash, created_at) and `notes` table (id, user_id, content, created_at)
- POST /api/register — creates user with bcrypt-hashed password (cost 12), starts session
- POST /api/login — validates credentials with bcrypt.compareSync, starts session
- POST /api/logout — destroys session, clears cookie
- GET /api/me — returns current session user or 401
- GET /api/protected — requires auth middleware, returns success or 401
- POST /api/notes — requires auth, creates note owned by session user
- GET /api/notes/:id — requires auth, returns note ONLY if user_id matches session user (403 otherwise)
- GET /api/notes — requires auth, returns all notes for session user
- GET /api/debug/users — returns all users with their password_hash values (for security review evidence — proves hashing)
- GET / — serves an HTML page with UI for register, login, logout, protected route access, and note creation
- Session config: express-session with crypto.randomBytes(32) secret, 24h maxAge, httpOnly, sameSite lax

**HTML UI must include:**
- Registration form with username + password inputs and Register button
- Login form with username + password inputs and Login button
- Status display showing "Not logged in" or "Logged in as: {username}"
- Logout button (visible when logged in)
- "Access Protected Route" button (visible when logged in)
- Note creation form (visible when logged in)
- JavaScript that checks session on page load via /api/me and updates UI accordingly
- All results displayed in named DOM elements so Puppeteer can assert against them

**Important UI element IDs (Puppeteer will target these):**
- `#status` — login status display
- `#reg-user`, `#reg-pass`, `#register-btn`, `#reg-result`
- `#login-user`, `#login-pass`, `#login-btn`, `#login-result`
- `#logout-btn`
- `#protected-btn`, `#protected-result`
- `#note-content`, `#create-note-btn`, `#notes-list`
- `#current-user` — shows username when logged in
- `#auth-section` — visible when logged out
- `#logged-in-section` — visible when logged in (class "hidden" when logged out)

Run on port 3847.

---

## PHASE 2 — BUILD THE PUPPETEER TEST SUITE

Create `test-auth.js` in the same project directory.

This must test ALL 10 MUST requirements from the pilot spec with real browser interactions.

**Create directories:** `screenshots/` and `logs/`

**For each test:**
1. Perform real Puppeteer UI interaction (type into fields, click buttons, navigate)
2. Assert expected behavior
3. Capture a full-page screenshot named `{NN}-{description}.png`
4. Log: what was done, what was expected, what was observed, PROVEN or NOT PROVEN

**Required test flows:**

### AUTH-1.01 — User can register with credentials
- Go to page, fill reg-user="alice", reg-pass="securePass123", click Register
- Assert: status shows "Logged in as: alice"
- Screenshot: `01-after-register.png`

### AUTH-1.02 — Credentials stored hashed, never plaintext
- Navigate to /api/debug/users
- Assert: password_hash starts with `$2a$` (bcrypt), length > 50, value is NOT "securePass123"
- Screenshot: `02-hashed-credentials.png`

### AUTH-1.03 — Login with valid credentials produces session
- Logout first, then login as alice/securePass123
- Assert: status shows logged in, connect.sid cookie exists
- Screenshot: `03-login-success.png`

### AUTH-1.04 — Invalid credentials rejected
- Logout, then try login with alice/wrongPassword
- Assert: error message displayed (contains "Invalid"), text is red, not logged in
- Screenshot: `04-invalid-credentials.png`

### AUTH-1.05 — Session persists across page refresh
- Login as alice, then page.reload()
- Assert: still logged in after refresh
- Screenshot: `05-after-refresh.png`

### AUTH-1.06 — Session persists across browser restart
- Login as alice, save cookies, close page
- Create new browser context, set saved session cookie, navigate to page
- Assert: still logged in with saved session
- Screenshot: `06-after-browser-restart.png`

### AUTH-1.07 — Logout invalidates session
- Login as alice, click Logout
- Assert: status shows "Not logged in"
- Then fetch /api/protected — assert 401
- Screenshot: `07-after-logout.png`

### AUTH-1.08 — Protected route inaccessible without auth
- New page (no login), fetch /api/protected
- Assert: 401 status
- Screenshot: `08-protected-denied.png`

### AUTH-1.09 — Authorization restricts resource to owner
- Register "bob" via API, bob creates a note via API, get note ID
- Login as alice in browser, try to fetch /api/notes/{bob's note ID}
- Assert: 403 status, "Access denied"
- Screenshot: `09-authorization-denied.png`

### AUTH-1.10 — Expired/invalid session tokens rejected
- New page, set a tampered connect.sid cookie value
- Navigate to page, try /api/protected
- Assert: 401, not logged in
- Screenshot: `10-invalid-session-rejected.png`

**Output:**
- Write `logs/test-run.log` with timestamped entries for every action
- Write `logs/results.json` with structured results: `{ results: [...], gate: "PASS"|"FAIL", timestamp }`
- Print summary table to console
- Exit code 0 = all PROVEN, exit code 1 = any NOT PROVEN

---

## PHASE 3 — EXECUTE

1. `cd ~/auth-pilot && npm install`
2. Start server: `node server.js` (in background or separate process)
3. Run tests: `node test-auth.js`
4. Confirm all 10 MUST requirements show PROVEN
5. Confirm all 10 screenshots exist in `screenshots/`
6. Confirm `logs/results.json` exists and shows gate: "PASS"

If any test fails, diagnose, fix the application (not the test), and re-run.

---

## PHASE 4 — SECURITY REVIEW

After tests pass, perform a structured security self-review.

**Check and document:**

1. **Credential storage:**
   - Open `server.js`, confirm bcrypt.hashSync with cost factor ≥ 10
   - Confirm no plaintext password stored anywhere (no field named "password" in DB, only "password_hash")
   - Confirm /api/debug/users shows bcrypt hashes, not plaintext

2. **Session management:**
   - Confirm session secret is crypto.randomBytes(32) — not a static string
   - Confirm cookie has httpOnly: true
   - Confirm cookie has sameSite: 'lax' or 'strict'
   - Confirm maxAge is set (not infinite)

3. **Vulnerability patterns checked:**
   - No plaintext password in logs, console.log, or error messages
   - No session token in URL parameters
   - No raw password in API responses
   - Password comparison uses bcrypt.compareSync (timing-safe)
   - Failed login returns generic "Invalid credentials" — does not reveal whether username or password was wrong

Record all findings. This is a self-review (minimum viable for initial domain proof per the pilot spec).

---

## PHASE 5 — GENERATE GOVERNANCE ARTIFACTS

Now switch to the framework repo: `cd` to your local clone of `cto-build-framework`.

### File 1: Validation Run Log
Create: `validation/runs/auth-authorization-AUTH-1-2026-03-18.md`

Use the template at `validation/templates/domain-validation-run-template.md`.

Fill in:
- Domain: Authentication / Authorization
- Project Name: AUTH-1 Minimal Auth Pilot
- Project Class: Standard
- Run Date: today's date
- Operator: Yosi Wizman (owner)
- Artifact Class: Class 3 — New Execution Artifact
- Goal: Prove the governance loop works for authentication/authorization
- Scope: Registration, login, session, logout, protected route, owner authorization
- Out of scope: OAuth, MFA, RBAC, password reset, rate limiting
- Environment: Mac Mini M4, Node.js version, Chrome version, exact details
- For each of the 10 MUST requirements: record what was done, what was observed, result
- Link to screenshots in evidence packet
- Verdict: PASS or FAIL based on results
- Classification declaration stating Class 3 constraints

### File 2: Evidence Packet
Create: `validation/evidence-packets/auth-authorization-AUTH-1-2026-03-18.md`

Use the template at `validation/templates/evidence-packet-template.md`.

Must include:
- Mapping of each AUTH-1 MUST requirement to its evidence (screenshot filename, log entry, observed behavior)
- Screenshot references for all 10 requirements
- Security review summary
- Statement of what this evidence proves and what it does NOT prove
- Explicit scope boundaries: "This evidence covers basic username/password auth with bcrypt hashing and express-session. It does not cover OAuth, MFA, RBAC, password reset, or enterprise auth patterns."

### File 3: Security Review Record
Embed in the evidence packet OR create as a separate section.

Must state:
- Review type: self-review
- Credential storage: bcrypt with cost factor 12, no plaintext
- Session: cryptographic secret, httpOnly, sameSite, expiring
- Vulnerabilities checked: plaintext storage (clear), token leakage (clear), timing-safe comparison (clear), error message information leakage (clear)
- Limitation: this is a self-review, not a professional security audit

### File 4: Reviewer Verdict
Create: `validation/reviews/auth-authorization-AUTH-1-review-2026-03-18.md`

Use the template at `validation/templates/reviewer-verdict-template.md`.

This verdict is PARTIAL because:
- The review is based on the operator's own evidence (not independent re-execution)
- Security review is self-review level
- Independent re-execution by a separate operator is outstanding

State clearly:
- What was reviewed
- What evidence was examined
- Verdict: PARTIAL
- Conditions for upgrade to PASS: independent re-execution + independent security review

---

## PHASE 6 — UPDATE DOMAIN MATRIX AND LEDGER

### Update `validation/domain-matrix.md`
Change the Authentication / Authorization row from:
```
| Authentication / Authorization | Untested | Doctrine exists | Domain overlay designed, no project built |
```
To:
```
| Authentication / Authorization | Partially Validated | AUTH-1 pilot — 10/10 MUST proven (self-review, no independent re-execution) | Basic username/password auth with bcrypt + express-session. No OAuth, MFA, or RBAC. Security self-review only. |
```

Do NOT set to Validated — that requires independent re-execution per the domain-matrix re-execution rules.

### Update `validation/validation-ledger.md`
Update the Authentication / Authorization row with:
- Current Status: **Partially Validated**
- Last Validation Run: link to the run log
- Evidence Packet: link to the evidence packet
- Reviewer Verdict: link to reviewer verdict — PARTIAL
- Notes: "AUTH-1 pilot complete. 10/10 MUST proven. Self-review security. Independent re-execution outstanding."

---

## PHASE 7 — COPY SCREENSHOTS INTO REPO

Copy the screenshots from the auth-pilot project into the framework repo:

```bash
mkdir -p validation/screenshots/auth-authorization-AUTH-1
cp ~/auth-pilot/screenshots/*.png validation/screenshots/auth-authorization-AUTH-1/
```

Also copy the test log:
```bash
cp ~/auth-pilot/logs/test-run.log validation/runs/auth-authorization-AUTH-1-test-log.txt
cp ~/auth-pilot/logs/results.json validation/runs/auth-authorization-AUTH-1-results.json
```

---

## PHASE 8 — COMMIT AND PUSH

Stage all new and modified files:

```bash
git add validation/runs/auth-authorization-AUTH-1* \
       validation/evidence-packets/auth-authorization-AUTH-1* \
       validation/reviews/auth-authorization-AUTH-1* \
       validation/screenshots/auth-authorization-AUTH-1/ \
       validation/domain-matrix.md \
       validation/validation-ledger.md

git commit -m "AUTH-1 validation run: Authentication/Authorization domain — 10/10 MUST proven

- Pilot: minimal auth system (register, login, session, logout, protected route, owner authorization)
- All 10 MUST requirements verified by Puppeteer with screenshots
- Security self-review: bcrypt hashing, httpOnly sessions, no plaintext
- Reviewer verdict: PARTIAL (no independent re-execution)
- Domain promoted: Untested → Partially Validated
- No other domain statuses changed"

git push
```

---

## PHASE 9 — OUTPUT SUMMARY

After everything is committed and pushed, output:

1. **System summary** — what was built (one paragraph)
2. **MUST requirements table** — all 10 with status, screenshot path, evidence reference
3. **Gate result** — PASS or FAIL
4. **Files created** — full list with paths
5. **Files modified** — domain-matrix.md, validation-ledger.md
6. **Gaps or failures** — anything that did not pass or could not be verified
7. **Confirmation** — "No proof claims were widened beyond what this run demonstrates"

---

## CRITICAL REMINDERS

- This is Artifact Class 3. Do not mix with Class 1 or Class 2 evidence.
- Do not set the domain to Validated. Partially Validated is the ceiling without independent re-execution.
- The security review is self-review. State this explicitly. Do not imply professional audit.
- Screenshots are required evidence. No screenshot = NOT PROVEN.
- If any MUST requirement fails, the gate is FAIL. Fix and re-run, or document the failure.
- Do not modify any other domain's status, any Appendix B content, or any existing evidence packets.
- Read the pilot spec before starting: `validation/pilot-specs/AUTH-1-authentication-authorization.md`
- Read the run template before writing artifacts: `validation/templates/domain-validation-run-template.md`
- Read the evidence packet template: `validation/templates/evidence-packet-template.md`
- Read the reviewer verdict template: `validation/templates/reviewer-verdict-template.md`

---

_This instruction file is a governance artifact. It documents what Claude Code was instructed to do. The execution evidence is what proves it was done._
