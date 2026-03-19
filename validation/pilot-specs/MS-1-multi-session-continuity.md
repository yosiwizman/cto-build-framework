# Pilot Spec: MS-1 — Multi-Session Continuity

**Type:** Validation pilot specification — pre-execution planning document
**Domain:** Multi-Session Continuity
**Current status:** Partially Validated (handoff protocol designed; no complete multi-session run on file)
**Date created:** 2026-03-18

---

## Purpose

Produce the first complete governed project that spans a real session break. Exercise the handoff protocol documented in `governance/llm-operating-discipline.md` Section 6 under real conditions, not simulation.

This pilot converts Multi-Session Continuity from Partially Validated to a candidate for Validated status.

---

## Current Proof Status

- Handoff protocol is designed and documented
- Both original pilots (task tracker, contact manager) were completed in single sessions
- No evidence packet exists for a multi-session governed build
- No reviewer verdict exists for this domain
- The domain cannot be cited as field-tested until this pilot (or equivalent) completes

Reference: `validation/domain-matrix.md` row "Multi-Session Continuity" and `validation/evidence-expansion-roadmap.md` Campaign 2.

---

## Scope Boundary

**In scope:**
- A Standard-class project (within the already-validated project category) built across exactly two sessions with a real session break
- Handoff document produced at end of session 1
- Session 2 begins from the handoff document, not from conversation memory
- Full governance loop: scope → architecture → build → verify → gate → release
- All MUST requirements reach Proven across the two sessions combined

**Out of scope:**
- Proving any new domain (backend, auth, payments, etc.) — the project must stay within Standard-class client-side scope so that session continuity is the only new variable
- More than two sessions — the first pilot proves one session break; multi-break continuity is a separate future validation
- Non-coder operator as orchestrator — this pilot may use the framework designer; independent non-coder operation is a separate validation goal
- Automated session handoff — the handoff is manual and document-based per current doctrine

---

## MUST Requirements

| ID | Requirement | Verification Method |
|----|-------------|-------------------|
| MS-1.01 | Project has at least 6 MUST requirements defined before build begins | Scope document review |
| MS-1.02 | Session 1 completes at least 3 MUST requirements to Proven status | Evidence packet — session 1 section |
| MS-1.03 | Session 1 ends with a filed handoff document following the protocol in `governance/llm-operating-discipline.md` Section 6 | Handoff artifact on file |
| MS-1.04 | Real session break occurs — not a simulated pause within a single session | Operator attestation with timestamps |
| MS-1.05 | Session 2 begins by reading the handoff document — not from conversation history or memory | Session 2 opening prompt references handoff document |
| MS-1.06 | Remaining MUST requirements reach Proven in session 2 | Evidence packet — session 2 section |
| MS-1.07 | No requirements were lost, duplicated, or contradicted across the session break | Cross-session requirement reconciliation in evidence packet |
| MS-1.08 | Release gate executed at end of session 2 with a scored verdict | Gate result on file |
| MS-1.09 | All MUST requirements at Proven at gate time | Gate scoring sheet |

---

## Exclusions / Non-Goals

- This pilot does not prove multi-session continuity for Complex, Domain-Heavy, or Specialist class projects
- This pilot does not prove that handoff works with a different operator in session 2
- This pilot does not prove that handoff works across different AI tools or models between sessions
- This pilot does not validate any domain beyond the project's own domain (which must be Standard-class client-side)

---

## Required Evidence Artifacts

| Artifact | Template | Filing Location |
|----------|----------|-----------------|
| Validation run log | `validation/templates/domain-validation-run-template.md` | `validation/runs/multi-session-continuity-MS-1-[date].md` |
| Handoff document (session 1 output) | Per `governance/llm-operating-discipline.md` Section 6 | Embedded in or linked from run log |
| Evidence packet | `validation/templates/evidence-packet-template.md` | `validation/evidence-packets/multi-session-continuity-MS-1-[date].md` |
| Reviewer verdict | `validation/templates/reviewer-verdict-template.md` | `validation/reviews/multi-session-continuity-MS-1-review-[date].md` |

All artifacts must declare Artifact Class 3 (New Execution Artifact) per `validation/domain-matrix.md` classification rules.

---

## Founder Verification Requirements

- Founder operates as orchestrator across both sessions
- Founder verifies each MUST requirement against the running application
- Founder signs off on the handoff document content before session 1 ends
- Founder confirms session 2 successfully resumed from the handoff without context loss

---

## Release / Gate Criteria

The release gate must:
- Cover all MUST requirements listed above
- Produce a scored verdict (PASS / FAIL)
- Be executed at the end of session 2, not retroactively
- Include explicit assessment of whether continuity was maintained across the break

A PASS requires: all MUST requirements at Proven, no requirement loss or contradiction across sessions, and handoff document on file.

---

## Specialist Review Requirements

None required for this pilot. Multi-session continuity does not trigger domain-specific specialist review. Standard reviewer verdict process applies.

---

## Promotion Criteria

This domain may be promoted from Partially Validated to Validated when:

1. This pilot (or equivalent) completes with a PASS gate verdict
2. All required evidence artifacts are filed
3. Reviewer verdict is filed (PARTIAL minimum; PASS if independent re-execution is included)
4. `validation/domain-matrix.md` is updated in the same commit as the reviewer verdict
5. `validation/validation-ledger.md` is updated to reflect new status and artifact links

The domain remains Partially Validated until all five conditions are met.

---

_This is a pre-execution planning document. It does not constitute evidence of validation. Filing this spec does not change the domain's current status._
