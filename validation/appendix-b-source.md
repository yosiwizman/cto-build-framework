# Appendix B — Domain Validation Status

**This file is the canonical repo-side source for Appendix B of *The CTO Build Book*.**

It is the authoritative version of the domain validation status table. The manuscript Appendix B must be drafted directly from this file — not from the README, not from memory, not from any other summary. Any edit to domain status, scope qualifiers, or disclosure language must be made here first, then reflected in the manuscript.

**Source of truth chain:**
- `validation/domain-matrix.md` — domain status labels and evidence sources
- `validation/evidence-coverage-matrix.md` — scope boundaries per domain (Part D)
- `validation/validation-ledger.md` — reviewer verdict states and evidence chain status
- `validation/appendix-b-publication-audit.md` — audit of manuscript Appendix B against this file

**Last updated:** 2026-03-17

---

## Disclosure

All five Validated domains listed below reflect pilot evidence produced during Pilot 1 (Task Tracker) and Pilot 2 (Contact Manager). These pilots predate the formal independent re-execution requirement now documented in `validation/domain-matrix.md`.

**Current reviewer verdicts for all five Validated domains are PARTIAL.** Independent re-execution — a separate, documented run by a party other than the original build operator — has not been completed for any domain. The Validated labels represent the historical pilot result, not a fully closed evidence chain.

This is the same disclosure that appears in the README scope note. Appendix B must carry it.

---

## Domain Validation Status Table

| Domain | Status | Evidence Source | Scope Boundary |
|--------|--------|----------------|----------------|
| CRUD / Local-State Applications | **Validated** (PARTIAL verdict) | Pilot 1 — Task Tracker (10/10 MUST proven) | Single-page app with localStorage only; no backend, no server persistence |
| Client-Side Multi-Page Apps | **Validated** (PARTIAL verdict) | Pilot 2 — Contact Manager (14/14 MUST proven) | Hash routing; client-side state only; no backend, no server |
| Search / Filtering | **Validated** (PARTIAL verdict) | Pilot 2 — Contact Manager | Name/company search and single category filter proven; Pilot 2 contact manager only; in-memory/localStorage; server-side search, faceted search, and pagination not tested |
| Form Validation | **Validated** (PARTIAL verdict) | Pilot 2 — Contact Manager: R-09 only | Client-side email format validation only (one field, one rule); no other field types; no required-field enforcement beyond email; no server-side validation tested |
| Responsive UI (Desktop + Mobile) | **Validated** (PARTIAL verdict) | Pilot 1 + Pilot 2: founder-verified | Founder-verified on desktop and mobile; device names, OS, and browser not recorded; physical device re-execution outstanding |
| Multi-Session Continuity | **Partially Validated** | Handoff protocol designed and documented | Both pilots completed in single sessions; no complete multi-session project run on file; no evidence packet filed |
| Authentication / Authorization | **Untested** | Doctrine exists | Domain overlay designed; no project built under governance |
| Backend / API / Database | **Untested** | Doctrine exists | Architecture patterns documented; no project built under governance |
| Payments / Compliance (PCI) | **Untested** | Doctrine exists | PCI overlay designed; no project built under governance |
| Production Deployment / Runtime | **Untested** | Doctrine exists | Deployment governance designed; no deployment exercised |
| CI / Branch / Merge Governance | **Untested** | Doctrine exists | Branch governance designed; no project exercised it |
| Swarm / Parallel Execution | **Untested** | Doctrine exists | Multi-agent orchestration doctrine exists; nothing exercised |
| External Integrations (Third-Party APIs) | **Untested** | No doctrine | No doctrine; no project |
| Real-Time / Event-Driven Systems | **Untested** | No doctrine | No doctrine; no project |
| VoIP / Telephony | **Untested** | No doctrine | No doctrine; no project |
| AI / LLM Workflow Integration | **Untested** | No doctrine | No doctrine; no project |

---

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Validated** | At least one project completed the full governance loop with all MUST requirements Proven. Current Validated entries have PARTIAL reviewer verdicts — independent re-execution is outstanding. |
| **Partially Validated** | Governance mechanisms designed and partially tested; no complete project through the full loop with filed evidence. |
| **Untested** | Governance doctrine may exist, but no project has been built or run under governance in this domain. |

**PARTIAL verdict:** A PARTIAL reviewer verdict means the reviewer evaluated filed documentation and pilot records but independent re-execution has not been completed. PARTIAL is the ceiling achievable through documentation review alone. Full Validated status requires an independent re-execution proof — see `validation/domain-matrix.md` for the re-execution requirement definition.

---

## What This Table Shows and Does Not Show

**What it shows:**
- The current historical validation result for 5 domains, bounded by the scope qualifiers above
- The current status of 1 domain under partial testing
- The untested range across 10 domains — 6 with doctrine, 4 without

**What it does not show:**
- That the framework is unproven — the core governance loop has been exercised through two complete pilot projects
- That the validated domains are broadly applicable beyond the stated scope
- That Form Validation covers general form behavior — it covers one email format rule (R-09) in one project
- That Responsive UI was verified with recorded device details — device names, OS, and browser were not captured; physical device re-execution is outstanding
- That any PARTIAL verdict has been closed — all five Validated domains are awaiting independent re-execution

The companion framework is available at: https://github.com/yosiwizman/cto-build-framework

It includes the full Domain Validation Matrix with specific evidence requirements for each domain and the exact criteria a new project must meet to extend the validation boundary into an untested domain.

---

## Maintenance Note

This file must be updated before any new manuscript revision that touches domain status claims. The update sequence is:

1. Update `validation/domain-matrix.md` (canonical source — domain status and evidence)
2. Update `validation/evidence-coverage-matrix.md` Part D (scope boundaries)
3. Update `validation/validation-ledger.md` (reviewer verdict state)
4. Update this file to match all three sources exactly
5. Re-run `validation/appendix-b-publication-audit.md` comparison table against the updated draft
6. Update the manuscript Appendix B from this file — not from the other sources directly

Do not update the manuscript from `domain-matrix.md` or the README directly. This file is the single bridge. Its purpose is to carry the scope qualifiers, disclosure language, and status definitions in the exact form the manuscript requires.

---

_Created: 2026-03-17. Source: `validation/domain-matrix.md`, `validation/evidence-coverage-matrix.md` Part D, `validation/validation-ledger.md`. One new file only. No domain status changes. No manuscript edits._
