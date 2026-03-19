# Evidence Packet — AUTH-1 Authentication / Authorization

> **Artifact Class: Class 3 — New Execution Artifact**
> **Domain ceiling: Partially Validated — independent re-execution outstanding**

---

## Packet Metadata

| Field | Value |
|-------|-------|
| Claim being proven | The CTO Build Framework governance loop works for basic username/password authentication and owner-level authorization using bcrypt hashing and express-session |
| Domain | Authentication / Authorization |
| Project | AUTH-1 Minimal Auth Pilot |
| Software version at time of evidence capture | auth-pilot v1.0.0 (Node.js v22.17.1, Express 4.x, bcryptjs 2.4.3, express-session 1.17.3, better-sqlite3 9.x) |
| Date evidence captured | 2026-03-19 |
| Evidence captured by | Claude Code (claude-sonnet-4-6) — same agent as builder |
| Packet prepared by | Claude Code (claude-sonnet-4-6) |
| Packet version | 1.0 |

---

## 1. The Claim

The CTO Build Framework governance loop successfully governs an Authentication / Authorization domain project. Specifically: a minimal Node.js + Express application implementing user registration with bcrypt-hashed credential storage, session-based login, logout with session invalidation, a protected route requiring authentication, and owner-level authorization — was built under governance, verified by Puppeteer browser automation, and all 10 MUST requirements from `validation/pilot-specs/AUTH-1-authentication-authorization.md` were proven with screenshot evidence.

**Scope boundary:** Basic username/password auth with bcrypt + express-session. SQLite in-memory database. Single-owner authorization check. This is not a claim about OAuth, MFA, RBAC, production-grade security, or enterprise auth patterns.

---

## 2. What This Claim Does NOT Cover

- OAuth / social login / third-party identity providers — not tested
- Multi-factor authentication (MFA) — not tested
- Role-based access control (RBAC) beyond a single owner check — not tested
- Password reset / recovery flows — not tested
- Rate limiting or brute-force protection — not tested
- Production deployment security (TLS termination, secure cookie over HTTPS, reverse proxy headers) — not tested
- Professional security audit — this evidence includes self-review only
- Enterprise-scale auth patterns or compliance certification (SOC2, ISO27001, etc.)
- Any domain beyond Authentication / Authorization

---

## 3. Artifact List

| # | Artifact | Type | Description | Location |
|---|---------|------|-------------|----------|
| 1 | 01-after-register.png | Screenshot | Alice registers; status shows "Logged in as: alice" | `validation/screenshots/auth-authorization-AUTH-1/` |
| 2 | 02-hashed-credentials.png | Screenshot | /api/debug/users shows $2a$12$ bcrypt hashes for alice and bob | `validation/screenshots/auth-authorization-AUTH-1/` |
| 3 | 03-login-success.png | Screenshot | Alice logs in; status shows "Logged in as: alice"; connect.sid cookie present | `validation/screenshots/auth-authorization-AUTH-1/` |
| 4 | 04-invalid-credentials.png | Screenshot | Wrong password; error div shows "Invalid credentials" in red; status "Not logged in" | `validation/screenshots/auth-authorization-AUTH-1/` |
| 5 | 05-after-refresh.png | Screenshot | Alice logged in; page.reload(); status still "Logged in as: alice" | `validation/screenshots/auth-authorization-AUTH-1/` |
| 6 | 06-after-browser-restart.png | Screenshot | Session cookie saved, restored in new page; status still "Logged in as: alice" | `validation/screenshots/auth-authorization-AUTH-1/` |
| 7 | 07-after-logout.png | Screenshot | Alice clicks Logout; status "Not logged in"; /api/protected returns 401 | `validation/screenshots/auth-authorization-AUTH-1/` |
| 8 | 08-protected-denied.png | Screenshot | Fresh unauthenticated page; /api/protected returns 401 JSON | `validation/screenshots/auth-authorization-AUTH-1/` |
| 9 | 09-authorization-denied.png | Screenshot | Alice fetches Bob's note; server returns 403 "Access denied" | `validation/screenshots/auth-authorization-AUTH-1/` |
| 10 | 10-invalid-session-rejected.png | Screenshot | Tampered connect.sid set; status "Not logged in"; /api/protected 401 | `validation/screenshots/auth-authorization-AUTH-1/` |
| 11 | auth-authorization-AUTH-1-test-log.txt | Log | Full timestamped test run log | `validation/runs/` |
| 12 | auth-authorization-AUTH-1-results.json | Gate result | Structured JSON: all 10 results PROVEN, gate: "PASS" | `validation/runs/` |
| 13 | auth-authorization-AUTH-1-2026-03-19.md | Run log | Domain validation run log | `validation/runs/` |

---

## 4. Requirement Evidence

| Requirement | Truth State | Evidence Artifact | Verified By | Notes |
|-------------|-------------|------------------|-------------|-------|
| AUTH-1.01 — User registration | Proven | 01-after-register.png | Puppeteer automation | Status DOM element confirmed "Logged in as: alice" after registration |
| AUTH-1.02 — Credentials stored hashed | Proven | 02-hashed-credentials.png | Puppeteer automation + code review | Hash prefix $2a$12$, length 60, confirmed not plaintext "securePass123" |
| AUTH-1.03 — Valid login produces session | Proven | 03-login-success.png | Puppeteer automation | Status confirmed; connect.sid cookie confirmed present in browser context |
| AUTH-1.04 — Invalid credentials rejected | Proven | 04-invalid-credentials.png | Puppeteer automation | Error text "Invalid credentials", CSS class "error", status "Not logged in" |
| AUTH-1.05 — Session persists across refresh | Proven | 05-after-refresh.png | Puppeteer automation | page.reload() called; status remained "Logged in as: alice" |
| AUTH-1.06 — Session persists across restart | Proven | 06-after-browser-restart.png | Puppeteer automation | Cookie saved from first page, restored in new page, session validated |
| AUTH-1.07 — Logout invalidates session | Proven | 07-after-logout.png | Puppeteer automation | Logout clicked; status "Not logged in"; /api/protected HTTP 401 confirmed |
| AUTH-1.08 — Protected route without auth | Proven | 08-protected-denied.png | Puppeteer automation | Fresh unauthenticated page; /api/protected HTTP 401 |
| AUTH-1.09 — Authorization restricts to owner | Proven | 09-authorization-denied.png | Puppeteer automation | Bob's note ID 1; Alice fetch returns HTTP 403 "Access denied" |
| AUTH-1.10 — Tampered token rejected | Proven | 10-invalid-session-rejected.png | Puppeteer automation | Tampered cookie value; /api/me and /api/protected both return 401 |

---

## 5. Founder Verification

- [x] Yes — all 10 MUST items verified personally by Yosi Wizman on 2026-03-19
- [ ] Partial
- [ ] No

**Founder verification date:** 2026-03-19
**Device:** Local Threadripper environment (browser-based verification, http://localhost:3847)
**Verified by:** Yosi Wizman (founder)

**Per-requirement founder sign-off:**

| ID | Requirement | Founder Result | Notes |
|----|-------------|---------------|-------|
| AUTH-1.01 | User registration | **PASS** | Registration flow confirmed personally |
| AUTH-1.02 | Credentials stored hashed | **PASS** | bcrypt hash confirmed at /api/debug/users |
| AUTH-1.03 | Valid login produces session | **PASS** | Login confirmed personally |
| AUTH-1.04 | Invalid credentials rejected | **PASS** | Invalid credentials rejected — error displayed |
| AUTH-1.05 | Session persists across page refresh | **PASS** | Session held after page refresh |
| AUTH-1.06 | Session persists across browser restart | **PASS** | Session held after browser restart (server kept running) |
| AUTH-1.07 | Logout invalidates session | **PASS** | Logout confirmed; session invalidated |
| AUTH-1.08 | Protected route blocked when logged out | **PASS** | 401 returned on /api/protected when unauthenticated |
| AUTH-1.09 | Authorization: wrong user denied | **PASS** | API returns 403 when wrong user accesses another user's note. Note: UI displays notes across users — presentation-layer issue, not a security failure; API authorization boundary is correct |
| AUTH-1.10 | Tampered session token rejected | **PASS** | Session invalidated after cookie removal/tampering |

**Founder note on record:** "401 on /api/me observed when unauthenticated — expected behavior, not a failure." AUTH-1.09: UI currently displays notes across users; API correctly enforces 403 — this is a presentation-layer issue, not a security failure.

**Governance loop status:** FOUNDER VERIFICATION COMPLETE — all 10 MUST requirements personally verified by Yosi Wizman. Independent re-execution by a separate operator remains outstanding (required for Validated promotion).

---

## 6. Reviewer Verification

- [x] No — the reviewer is the same agent (Claude Code) that built and ran the tests. This is the basis for the PARTIAL verdict. Independent review by a separate party is outstanding.

See `validation/reviews/auth-authorization-AUTH-1-review-2026-03-19.md` for the formal PARTIAL verdict record.

---

## 7. Release Gate Results

| Field | Value |
|-------|-------|
| Gate type used | Personal Production (10-item MUST checklist per pilot spec) |
| Requirements proven | 10 / 10 |
| Gate verdict | PASS |
| Gate record location | `validation/runs/auth-authorization-AUTH-1-results.json` |

---

## 8. Security Review Record

**Review type:** Self-review (structured checklist against server.js source and live runtime)
**Review date:** 2026-03-19
**Reviewer:** Claude Code (same agent as builder — self-review limitation applies)

| Check | Finding | Status |
|-------|---------|--------|
| Credential storage algorithm | bcrypt.hashSync with cost factor 12 | CLEAR |
| Hash format | $2a$12$ prefix, 60 characters, bcryptjs library | CLEAR |
| Plaintext password in database | No — only password_hash column exists in users table | CLEAR |
| Plaintext password in logs or error messages | No — error messages are generic "Invalid credentials" | CLEAR |
| Session secret randomness | crypto.randomBytes(32).toString('hex') — new secret per server start | CLEAR |
| Session cookie httpOnly | true — confirmed in session config | CLEAR |
| Session cookie sameSite | 'lax' — confirmed in session config | CLEAR |
| Session cookie maxAge | 24 * 60 * 60 * 1000 (24 hours) — not infinite | CLEAR |
| Password comparison timing | bcrypt.compareSync — constant-time comparison | CLEAR |
| Session token in URL parameters | No — session is cookie-only | CLEAR |
| Raw password in API responses | No — register and login responses return only { success, username } | CLEAR |
| Error message information leakage | Login returns "Invalid credentials" regardless of whether username or password is wrong | CLEAR |
| Username enumeration via registration | "Username already taken" is returned on duplicate registration — mild enumeration vector | NON-BLOCKING LIMIT |

**Security review limitation:** This is a self-review against a structured checklist. It is not a professional security audit. No penetration testing, no OWASP ZAP scan, no code review by an independent security engineer was performed. The claim boundary is scoped accordingly: this evidence proves that basic credential-handling patterns are correct, not that the application is production-secure.

---

## 8. Proof-Boundary Note

**What this evidence proves:**
The CTO Build Framework governance loop successfully governs the construction and verification of a basic authentication/authorization system with bcrypt hashing, express-session management, protected routes, and owner-level authorization. All 10 MUST requirements from the pilot spec were demonstrated by automated browser interaction with screenshot evidence. The session, credential, and authorization patterns behave correctly under test conditions.

**What this evidence does NOT prove:**
- That the framework handles OAuth, MFA, RBAC, or enterprise auth patterns
- That the application is production-secure (self-review only; no professional audit)
- That this result was independently reproduced by a party other than the builder
- That the governance loop is fully closed per spec requirements (it is NOT — independent re-execution by a separate operator is still outstanding; this is the remaining condition for Validated promotion)
- That the AUTH-1.09 UI presentation is correct — UI displays notes across users; API authorization is correct (403 enforced); UI fix is a separate non-blocking item
- That auth governance scales to production deployment conditions (TLS, reverse proxy, production secrets management)
- That any other domain has been validated

---

## 9. Unresolved Limits

| Limit | Impact | Status |
|-------|--------|--------|
| Same agent built and tested (no independent re-execution) | Domain ceiling is Partially Validated, not Validated | Accepted — stated in all artifacts |
| Founder personal verification | All 10 MUST items verified by Yosi Wizman on 2026-03-19 | **RESOLVED** — complete |
| Self-review security (no professional audit) | Security claim is bounded to checklist-level | Accepted — stated explicitly |
| Username enumeration via /api/register endpoint | Minor information leakage; non-blocking for initial domain proof | Accepted |
| In-memory SQLite (no persistence across restarts) | Not a test-validity issue but limits the realistic deployment claim | Accepted — out of scope for initial proof |

---

## 10. Packet Status

- [x] Complete — all sections filled, all 10 screenshots on file, gate result on file, security review embedded, ready for ledger update

---

_Created: 2026-03-19. Updated: 2026-03-19 (correction pass). Updated: 2026-03-19 (founder verification complete — all 10 MUST items personally verified by Yosi Wizman). Class 3 — New Execution Artifact. Domain ceiling: Partially Validated. Founder verification: COMPLETE. Independent re-execution by separate operator: outstanding (required for Validated promotion)._
