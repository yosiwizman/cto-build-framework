# Pilot Spec: AUTH-1 — Authentication / Authorization

**Type:** Validation pilot specification — pre-execution planning document
**Domain:** Authentication / Authorization
**Current status:** Untested (domain overlay designed; no project built under governance)
**Date created:** 2026-03-18

---

## Purpose

Produce the first governed build of a project with real user authentication and access control. This pilot proves that the governance loop handles identity, session management, and authorization boundaries — capabilities present in nearly every production application.

---

## Current Proof Status

- Domain overlay is designed within governance doctrine
- No project with authentication or authorization has been built under the governance loop
- No evidence packet, run log, or reviewer verdict exists for this domain
- The domain cannot be cited as governed, validated, or safe under this framework until this pilot (or equivalent) completes

Reference: `validation/domain-matrix.md` row "Authentication / Authorization" and `validation/evidence-expansion-roadmap.md` Priority 5.

---

## Scope Boundary

**In scope:**
- User registration with credential storage (hashed — never plaintext)
- User login producing a session or token
- Session persistence across page refresh or browser restart
- Logout that invalidates the session or token
- At least one protected route or resource that requires authentication to access
- At least one authorization check: a resource or action restricted to a specific user or role
- Error handling for invalid credentials, expired sessions, and unauthorized access attempts

**Out of scope:**
- OAuth / social login / third-party identity providers — those add external integration complexity beyond the core auth domain
- Multi-factor authentication (MFA) — future scope after basic auth is proven
- Role-based access control (RBAC) beyond a single authorization check — future scope
- Password reset / recovery flows — useful but not required for initial domain proof
- Rate limiting or brute-force protection — operational security, separate from auth governance proof
- Payment or compliance integration — separate domain (PCI-1)

---

## MUST Requirements

| ID | Requirement | Verification Method |
|----|-------------|-------------------|
| AUTH-1.01 | User can register with credentials | Founder verification — complete registration flow |
| AUTH-1.02 | Credentials are stored hashed, never in plaintext | Code review + founder verification — inspect storage mechanism |
| AUTH-1.03 | User can log in with valid credentials and receive a session/token | Founder verification — log in, confirm session exists |
| AUTH-1.04 | Invalid credentials are rejected with an appropriate error | Founder verification — attempt login with wrong password |
| AUTH-1.05 | Session persists across page refresh | Founder verification — refresh page while logged in, confirm session holds |
| AUTH-1.06 | Session persists across browser restart | Founder verification — close and reopen browser, confirm session holds |
| AUTH-1.07 | Logout invalidates the session/token | Founder verification — log out, confirm protected routes are inaccessible |
| AUTH-1.08 | At least one route or resource is protected — inaccessible without authentication | Founder verification — attempt access while logged out, confirm denial |
| AUTH-1.09 | At least one authorization check restricts a resource to its owner or authorized role | Founder verification — attempt access as wrong user, confirm denial |
| AUTH-1.10 | Expired or invalid session tokens are rejected | Founder verification — use expired/tampered token, confirm rejection |

---

## Exclusions / Non-Goals

- This pilot does not prove OAuth, social login, or federated identity governance
- This pilot does not prove MFA governance
- This pilot does not prove comprehensive RBAC or permission matrix governance
- This pilot does not prove that auth governance scales to enterprise-level access control
- This pilot does not validate any domain beyond Authentication / Authorization

---

## Required Evidence Artifacts

| Artifact | Template | Filing Location |
|----------|----------|-----------------|
| Validation run log | `validation/templates/domain-validation-run-template.md` | `validation/runs/auth-authorization-AUTH-1-[date].md` |
| Evidence packet | `validation/templates/evidence-packet-template.md` | `validation/evidence-packets/auth-authorization-AUTH-1-[date].md` |
| Security review record | See Specialist Review section | Embedded in or linked from evidence packet |
| Reviewer verdict | `validation/templates/reviewer-verdict-template.md` | `validation/reviews/auth-authorization-AUTH-1-review-[date].md` |

All artifacts must declare Artifact Class 3 (New Execution Artifact).

---

## Founder Verification Requirements

- Founder verifies the full registration → login → session → logout → denial cycle personally
- Founder verifies that invalid credentials, expired sessions, and unauthorized access all produce correct denial responses
- Founder confirms credential storage uses hashing (code-level check with assistance if needed — the verification is that plaintext is not stored, not that the founder understands the hashing algorithm)
- Founder signs off on each MUST requirement individually in the evidence packet

---

## Release / Gate Criteria

The release gate must:
- Cover all 10 MUST requirements
- Produce a scored verdict (PASS / FAIL)
- Include explicit confirmation that credential storage was checked for plaintext absence
- Include explicit confirmation that session invalidation was tested after logout
- Include the security review record (see below)

A PASS requires: all MUST requirements at Proven, evidence packet filed, security review on record, and no untested MUST requirements.

---

## Specialist Review Requirements

**Security review is required for this pilot.**

Authentication is a security-sensitive domain. The governance loop must include a security review step before the release gate. This review may be:

- A structured self-review against a security checklist (minimum viable for initial proof)
- A review by a security-knowledgeable party (stronger evidence)
- A professional security audit (strongest evidence, not required for initial domain proof)

The review must cover at minimum:
- Credential storage method (hashing algorithm, salt usage)
- Session/token generation method (randomness, expiration)
- Known vulnerability patterns (plaintext storage, session fixation, token leakage in URLs)

The review record must be filed as part of the evidence packet. The level of review (self-review, peer review, professional audit) must be stated explicitly — the claim boundary will be scoped accordingly.

---

## Promotion Criteria

This domain may be promoted from Untested to Validated when:

1. This pilot (or equivalent) completes with a PASS gate verdict
2. All required evidence artifacts are filed, including security review record
3. Reviewer verdict is filed
4. Independent re-execution proof is on file
5. `validation/domain-matrix.md` is updated in the same commit as the reviewer verdict
6. `validation/validation-ledger.md` is updated to reflect new status and artifact links

If the security review was self-review only, the claim boundary must note this limitation. A professionally audited pilot produces a stronger claim than a self-reviewed one, but both satisfy the minimum promotion threshold.

The domain remains Untested until all conditions are met.

---

_This is a pre-execution planning document. It does not constitute evidence of validation. Filing this spec does not change the domain's current status._
