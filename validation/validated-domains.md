> **Legacy notice:** This file is a pre-template narrative summary produced before the canonical evidence infrastructure existed. It is preserved as a historical record only. For current validation status, canonical evidence packets, and reviewer verdicts, see:
> - `validation/domain-matrix.md` — authoritative domain status and re-execution requirement
> - `validation/evidence-packets/` — formal evidence packets (all currently incomplete; screenshots not in repo)
> - `validation/reviews/` — reviewer verdicts (all currently PARTIAL; independent re-execution outstanding)
> - `validation/validation-ledger.md` — current status ledger
>
> Claims in this file predate the re-execution requirement and the PARTIAL-verdict findings. Do not cite this file as current evidence.

# Validated Domains

These domains have been fully validated through at least one project that completed the entire governance loop with all MUST requirements at Proven and a passing release gate.

## CRUD / Local-State Applications

**Validated by:** Pilot 1 — Task Tracker
**Requirements:** 10 MUST, all Proven
**Gate verdict:** PASS (Confidence: 28/35, Sufficiency: 16/20)
**Evidence:** Founder-verified with screenshots and test records on file
**What was proven:** Basic data operations (create, read, update, delete), localStorage persistence, single-page application structure, filter functionality

## Client-Side Multi-Page Applications

**Validated by:** Pilot 2 — Contact Manager
**Requirements:** 14 MUST, all Proven
**Gate verdict:** PASS (Confidence: 27/35, Sufficiency: 15/20)
**Evidence:** Founder-verified with screenshots and test records on file
**What was proven:** Client-side hash routing, multi-page navigation, shared state across views, data model with multiple fields

## Search / Filtering

**Validated by:** Pilot 2 — Contact Manager
**What was proven:** Real-time search by name and company, category-based filtering, combined search and filter behavior

## Form Validation

**Validated by:** Pilot 2 — Contact Manager
**What was proven:** Email format validation on contact forms, client-side input validation

## Responsive UI (Desktop + Mobile)

**Validated by:** Both pilots
**What was proven:** Both applications verified by founder on desktop and mobile devices, layout adapts correctly to screen sizes
