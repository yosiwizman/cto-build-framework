# Pilot Spec: API-1 — Backend / API / Database

**Type:** Validation pilot specification — pre-execution planning document
**Domain:** Backend / API / Database
**Current status:** Untested (doctrine exists; architecture patterns documented; no project built under governance)
**Date created:** 2026-03-18

---

## Purpose

Produce the first governed build of a project with a real backend server, API endpoints, and database persistence. This pilot extends the proof boundary from client-side local-state applications to server-side systems.

This is the most natural next expansion of the validated range. It covers the largest unvalidated category of production software.

---

## Current Proof Status

- Architecture patterns are documented in governance doctrine
- No project with a backend, API, or database has been built under the governance loop
- No evidence packet, run log, or reviewer verdict exists for this domain
- The domain cannot be cited as validated, proven, or field-tested until this pilot (or equivalent) completes

Reference: `validation/domain-matrix.md` row "Backend / API / Database" and `validation/evidence-expansion-roadmap.md` Priority 4.

---

## Scope Boundary

**In scope:**
- A project with a real backend server (Node.js, Python, or equivalent)
- At least 3 REST or equivalent API endpoints serving data to a client
- A real database (SQL or NoSQL) with persistent storage — not localStorage, not in-memory-only
- CRUD operations through the API layer with database persistence
- Error handling for common failure modes (invalid input, missing records, server errors)
- Full governance loop: scope → architecture → build → verify → gate → release

**Out of scope:**
- Authentication or authorization — that is a separate domain (AUTH-1)
- Third-party API integrations — that is a separate domain
- Production deployment to a public server — that is a separate domain (DEPLOY-1); this pilot may run locally or in a development environment
- Real-time / WebSocket functionality
- Payment processing
- Performance testing or load testing
- Database migration governance (future scope)

---

## MUST Requirements

| ID | Requirement | Verification Method |
|----|-------------|-------------------|
| API-1.01 | Backend server starts and serves API requests | Founder verification — server running, endpoint reachable |
| API-1.02 | At least 3 API endpoints defined and functional | Founder verification — each endpoint tested with real requests |
| API-1.03 | Database stores data persistently across server restarts | Founder verification — create data, restart server, confirm data survives |
| API-1.04 | Create operation: data sent via API is written to database | Founder verification — API call followed by database confirmation |
| API-1.05 | Read operation: data retrieved via API matches database contents | Founder verification — compare API response to database state |
| API-1.06 | Update operation: modified data sent via API updates database record | Founder verification — update call followed by read confirmation |
| API-1.07 | Delete operation: delete request via API removes database record | Founder verification — delete call followed by read confirmation of absence |
| API-1.08 | Invalid input returns appropriate error response, not a crash | Founder verification — send malformed request, confirm error response |
| API-1.09 | Missing record request returns appropriate error response | Founder verification — request nonexistent ID, confirm 404 or equivalent |
| API-1.10 | A client application successfully consumes the API | Founder verification — client displays data from API |

---

## Exclusions / Non-Goals

- This pilot does not prove database migration governance
- This pilot does not prove multi-database or distributed database patterns
- This pilot does not prove API versioning or backward compatibility governance
- This pilot does not prove that the governance system handles backend projects at scale — it proves one complete governed backend build
- This pilot does not validate any domain beyond Backend / API / Database

---

## Required Evidence Artifacts

| Artifact | Template | Filing Location |
|----------|----------|-----------------|
| Validation run log | `validation/templates/domain-validation-run-template.md` | `validation/runs/backend-api-database-API-1-[date].md` |
| Evidence packet | `validation/templates/evidence-packet-template.md` | `validation/evidence-packets/backend-api-database-API-1-[date].md` |
| Reviewer verdict | `validation/templates/reviewer-verdict-template.md` | `validation/reviews/backend-api-database-API-1-review-[date].md` |

All artifacts must declare Artifact Class 3 (New Execution Artifact).

---

## Founder Verification Requirements

- Founder verifies each API endpoint by making real requests (via browser, curl, Postman, or equivalent)
- Founder verifies database persistence by confirming data survives a server restart
- Founder verifies error handling by sending invalid or missing-record requests
- Founder verifies client-API integration by confirming the client displays API-sourced data
- Founder signs off on each MUST requirement individually in the evidence packet

---

## Release / Gate Criteria

The release gate must:
- Cover all 10 MUST requirements
- Produce a scored verdict (PASS / FAIL)
- Include explicit confirmation that data persistence was tested across server restart
- Include explicit confirmation that error responses were verified for invalid and missing-record cases

A PASS requires: all MUST requirements at Proven, evidence packet filed, and no untested MUST requirements.

---

## Specialist Review Requirements

None required for this pilot at the current scope. Backend / API / Database at this level does not trigger specialist review. If the pilot scope were expanded to include security-sensitive operations, production deployment, or compliance-relevant data handling, specialist review requirements would apply.

---

## Promotion Criteria

This domain may be promoted from Untested to Validated when:

1. This pilot (or equivalent) completes with a PASS gate verdict
2. All required evidence artifacts are filed
3. Reviewer verdict is filed
4. Independent re-execution proof is on file (per `validation/domain-matrix.md` re-execution requirement)
5. `validation/domain-matrix.md` is updated in the same commit as the reviewer verdict
6. `validation/validation-ledger.md` is updated to reflect new status and artifact links

The domain remains Untested until all conditions are met. A PARTIAL reviewer verdict (documentation review without re-execution) moves the domain to Partially Validated at most.

---

_This is a pre-execution planning document. It does not constitute evidence of validation. Filing this spec does not change the domain's current status._
