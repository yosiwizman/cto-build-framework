# Domain Validation Run — AUTH-1 Authentication / Authorization

> **Artifact Class: Class 3 — New Execution Artifact**
> Run date: 2026-03-19

---

## Run Metadata

| Field | Value |
|-------|-------|
| Domain | Authentication / Authorization |
| Project Name | AUTH-1 Minimal Auth Pilot |
| Project Class | Standard |
| Run Date | 2026-03-19 |
| Operator | Claude Code (claude-sonnet-4-6) — AI agent executing on behalf of Yosi Wizman (owner) |
| Reviewer (if separate) | Same operator — see PARTIAL verdict declaration |
| Run Status | Complete |

---

## Artifact Classification

| Field | Value |
|-------|-------|
| Artifact Class | **Class 3 — New Execution Artifact** |
| Source Artifact Path | `~/auth-pilot/` (outside framework repo — temporary build directory) |
| Execution Context | New independent validation run |

**Classification Declaration:**

> "This run uses a **Class 3** artifact. Results from this run must be evaluated under the constraints defined in `validation/domain-matrix.md` — Artifact Classification. Specifically: results from a Class 3 run may produce new evidence toward domain status. However, the reviewer verdict for this run is PARTIAL because the same agent (Claude Code) both built the application and executed the tests. Independent re-execution by a separate operator has not been completed. The domain may not be promoted above Partially Validated until independent re-execution is on file."

---

## 1. Goal

Prove that the CTO Build Framework governance loop handles the Authentication / Authorization domain — specifically: user registration with hashed credentials, session-based login, logout invalidation, protected route enforcement, and owner-level authorization — using a minimal Node.js + Express application verified by Puppeteer browser automation.

---

## 2. Hypothesis

The governance loop will successfully govern an auth implementation. All 10 MUST requirements will be provable by automated browser interaction. The bcrypt + express-session stack is well-established and the test surface is bounded and deterministic.

---

## 3. Scope

**In scope:**
- User registration with bcrypt-hashed credential storage
- Login with valid credentials producing an express-session cookie
- Session persistence across page refresh
- Session persistence simulated across browser restart (cookie save/restore)
- Logout that destroys the session and invalidates subsequent access
- Protected route that returns 401 when unauthenticated
- Owner-level authorization: cross-user note access returns 403
- Tampered/invalid session cookie rejection

**Out of scope:**
- OAuth / social login / federated identity
- Multi-factor authentication (MFA)
- Role-based access control (RBAC) beyond single-owner check
- Password reset / recovery flows
- Rate limiting or brute-force protection
- Payment or compliance integration
- Production deployment hardening (TLS, reverse proxy)

---

## 4. Environment

| Field | Value |
|-------|-------|
| Tools used | Node.js, Express, better-sqlite3, bcryptjs, express-session, Puppeteer |
| Browser / Runtime | Puppeteer headless Chromium (bundled with puppeteer@21.x), Node.js v22.17.1 |
| Device | Windows 11 Pro (local machine) |
| Git branch | master (framework repo) |
| Build directory | `~/auth-pilot/` (outside repo) |
| Database | SQLite in-memory (better-sqlite3) |
| Server port | 3847 |

---

## 5. Toolchain

- AI model / version: Claude Sonnet 4.6 (claude-sonnet-4-6) via Claude Code
- Editor / coding tool: Claude Code CLI
- Build tool: npm / Node.js
- Test method: Puppeteer browser automation — real browser interactions, screenshot evidence

---

## 6. Slice Plan

| Slice | Description | Status | Notes |
|-------|-------------|--------|-------|
| 1 | server.js — Express app with SQLite, bcrypt, sessions | Built / Verified | All endpoints implemented and running |
| 2 | HTML UI with all required DOM element IDs | Built / Verified | All Puppeteer target IDs confirmed present |
| 3 | test-auth.js — 10-test Puppeteer suite | Built / Verified | Required logout-before-login fix applied after first run |
| 4 | Full test execution | Complete | 10/10 PROVEN, gate PASS |

---

## 7. Risks and Unknowns

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| Browser session shared across Puppeteer pages | High | Added explicit /api/logout before each test needing clean state |
| In-memory DB lost on server restart | Known/accepted | Entire run executed in single server session |
| Headless Chrome not available | Low | Puppeteer bundles Chromium; confirmed working |
| Username enumeration via registration endpoint | Confirmed | Documented as non-blocking limit in evidence packet |

---

## 8. Checkpoints

| Checkpoint | Slice | Description |
|-----------|-------|-------------|
| 1 | Slice 1–2 | server.js and HTML UI complete; server responding on port 3847 |
| 2 | Slice 3 | test-auth.js written; first run revealed session-sharing bug (logout fix needed) |
| 3 | Slice 4 | Fix applied; full clean run completed; 10/10 PROVEN |

---

## 9. Test Protocol

| Requirement | Test Method | Who Verifies |
|-------------|------------|--------------|
| AUTH-1.01 — Registration | Puppeteer: fill form, click Register, assert status text | Puppeteer automation + screenshot |
| AUTH-1.02 — Hashed storage | Puppeteer: navigate to /api/debug/users, assert $2a$ prefix, length >50, not plaintext | Puppeteer automation + screenshot |
| AUTH-1.03 — Valid login + session | Puppeteer: login, assert status text + connect.sid cookie | Puppeteer automation + screenshot |
| AUTH-1.04 — Invalid credentials rejected | Puppeteer: wrong password, assert error element class + text | Puppeteer automation + screenshot |
| AUTH-1.05 — Session across refresh | Puppeteer: login, page.reload(), assert still logged in | Puppeteer automation + screenshot |
| AUTH-1.06 — Session across restart | Puppeteer: login, save cookie, new page, restore cookie, assert still logged in | Puppeteer automation + screenshot |
| AUTH-1.07 — Logout invalidation | Puppeteer: logout, assert "Not logged in" + /api/protected returns 401 | Puppeteer automation + screenshot |
| AUTH-1.08 — Protected route without auth | Puppeteer: fresh page, fetch /api/protected, assert 401 | Puppeteer automation + screenshot |
| AUTH-1.09 — Owner authorization | Puppeteer: register bob, create note, alice fetches bob's note, assert 403 | Puppeteer automation + screenshot |
| AUTH-1.10 — Tampered session rejected | Puppeteer: set tampered connect.sid, navigate, assert "Not logged in" + 401 | Puppeteer automation + screenshot |

---

## 10. Result Summary

| Field | Value |
|-------|-------|
| Slices completed | 4 / 4 planned |
| Requirements Proven | 10 / 10 MUST |
| Gate verdict | PASS |
| Unexpected outcomes | Session shared across Puppeteer pages (expected in browser context, not a bug — required explicit logout in test setup) |
| Scope drift incidents | None |

---

## 11. Artifact Links

| Artifact | Type | Location |
|---------|------|----------|
| Screenshot 01-after-register.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/01-after-register.png` |
| Screenshot 02-hashed-credentials.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/02-hashed-credentials.png` |
| Screenshot 03-login-success.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/03-login-success.png` |
| Screenshot 04-invalid-credentials.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/04-invalid-credentials.png` |
| Screenshot 05-after-refresh.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/05-after-refresh.png` |
| Screenshot 06-after-browser-restart.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/06-after-browser-restart.png` |
| Screenshot 07-after-logout.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/07-after-logout.png` |
| Screenshot 08-protected-denied.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/08-protected-denied.png` |
| Screenshot 09-authorization-denied.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/09-authorization-denied.png` |
| Screenshot 10-invalid-session-rejected.png | Screenshot | `validation/screenshots/auth-authorization-AUTH-1/10-invalid-session-rejected.png` |
| Test run log | Log | `validation/runs/auth-authorization-AUTH-1-test-log.txt` |
| Results JSON | Gate result | `validation/runs/auth-authorization-AUTH-1-results.json` |
| Evidence packet | Evidence | `validation/evidence-packets/auth-authorization-AUTH-1-2026-03-19.md` |
| Reviewer verdict | Verdict | `validation/reviews/auth-authorization-AUTH-1-review-2026-03-19.md` |

---

## 12. Verdict

- [x] **Partially** — all 10 MUST requirements Proven by Puppeteer automation; gate PASS; evidence on file. Verdict is PARTIAL because the same operator (Claude Code agent) both built the application and executed the tests. Independent re-execution by a separate party has not been completed.

**Conditions:**
- Independent re-execution required before domain may be promoted to Validated
- Security review is self-review level (not professional audit)
- Username enumeration via registration endpoint is a known non-blocking limit

---

## 13. Next Action

- [x] Copy screenshots to `validation/screenshots/auth-authorization-AUTH-1/`
- [x] File evidence packet to `validation/evidence-packets/`
- [x] File reviewer verdict (PARTIAL) to `validation/reviews/`
- [x] Update `validation/domain-matrix.md` — Untested → Partially Validated (separate commit)
- [x] Update `validation/validation-ledger.md` (same commit as domain-matrix update)
- [ ] Independent re-execution by a separate operator — OUTSTANDING
- [ ] Founder personal verification of full registration → login → session → logout → denial cycle per pilot spec — OUTSTANDING (Puppeteer automation does not satisfy the spec's founder verification requirement)

**Assigned to:** Yosi Wizman (owner)
**Target date:** To be scheduled by owner

**Governance loop status:** NOT CLOSED — governance loop cannot be called closed until founder personally verifies all 10 MUST requirements per pilot spec AND independent re-execution is on file.

---

_Created: 2026-03-19. Updated: 2026-03-19 (correction pass — Operator field corrected; founder verification gap elevated; governance loop closure status added). Class 3 — New Execution Artifact. Domain ceiling: Partially Validated. Governance loop NOT closed per spec requirements. Founder personal verification outstanding. Independent re-execution outstanding._
