# Pilot Spec: COM-1 — Commercial Release Gate

**Type:** Validation pilot specification — pre-execution planning document
**Domain:** Commercial Release Governance
**Current status:** Untested (release gate doctrine exists; only the personal-use gate has been field-tested in the pilots)
**Date created:** 2026-03-18

---

## Purpose

Exercise the full commercial release gate in a customer-facing context. This pilot proves that the governance loop handles the additional requirements that separate a personal project release from a release that real users will depend on: monitoring, support readiness, load expectations, compliance checks, and customer-facing quality verification.

The current pilots validated the personal release gate. This pilot validates the commercial release gate.

---

## Current Proof Status

- Release gate doctrine exists and has been exercised at the personal level (both pilots passed personal release gates)
- The commercial release gate is documented in governance but has never been exercised in a customer-facing release
- No evidence packet, run log, or reviewer verdict exists for a commercial release
- The commercial release gate cannot be cited as field-proven across domains until this pilot (or equivalent) completes

Reference: `validation/domain-matrix.md` and `validation/evidence-expansion-roadmap.md` Priority queue. The commercial release gate is described in `governance/release-gates.md`.

---

## Scope Boundary

**In scope:**
- A project released to real users (not just the founder) under governed release procedures
- Commercial release gate checklist executed before release, including:
  - monitoring or error-tracking setup confirmed
  - support channel or contact path defined
  - load expectations documented (even if simple — "expected 10 users")
  - privacy or terms-of-service requirements addressed if applicable
  - customer-facing quality verification (the application works acceptably for the target audience)
- Post-release verification: founder confirms the application is accessible and functional for users after release
- At least one real user (not the founder) accesses the application after release

**Out of scope:**
- High-scale load testing or performance benchmarking — future scope
- A/B testing or feature flagging governance
- SLA or uptime commitment governance
- Paid subscription or revenue-generating release — PCI-1 covers payment; this pilot covers the release governance layer
- Regulatory compliance beyond basic privacy/ToS — domain-specific compliance (healthcare, finance) is separate
- Marketing launch governance — this pilot covers the technical release gate, not the marketing launch process

**Dependency note:** This pilot naturally follows DEPLOY-1 (production deployment). A commercial release requires a production environment. Running COM-1 without DEPLOY-1 first would mean the commercial gate is exercised on a locally-served application, which weakens the proof value.

---

## MUST Requirements

| ID | Requirement | Verification Method |
|----|-------------|-------------------|
| COM-1.01 | Application is deployed and accessible to users other than the founder | Founder verification + at least one external user access confirmation |
| COM-1.02 | Commercial release gate checklist is executed before release | Checklist artifact on file |
| COM-1.03 | Monitoring or error-tracking is configured and confirmed operational | Founder verification — confirm monitoring dashboard or error-tracking tool is receiving data |
| COM-1.04 | Support channel or contact path is defined and reachable | Founder verification — confirm users can reach support |
| COM-1.05 | Load expectation is documented (number of expected users, even if small) | Documentation in release gate checklist |
| COM-1.06 | Privacy or terms-of-service requirements are addressed (even if "not applicable" — the assessment must be made) | Assessment on file in release gate checklist |
| COM-1.07 | At least one real user (not the founder) has accessed the application post-release | User access evidence — screenshot, log entry, or user confirmation |
| COM-1.08 | Post-release verification confirms the application functions correctly for external users | Founder verification — confirm core functionality after release |
| COM-1.09 | Release gate produces a scored verdict (PASS / FAIL) covering all commercial criteria | Gate result on file |

---

## Exclusions / Non-Goals

- This pilot does not prove commercial release governance at scale (hundreds or thousands of users)
- This pilot does not prove SLA or uptime governance
- This pilot does not prove paid-product release governance (that requires PCI-1)
- This pilot does not prove regulatory-specific release governance (healthcare, financial, etc.)
- This pilot does not validate any domain beyond Commercial Release Governance

---

## Required Evidence Artifacts

| Artifact | Template | Filing Location |
|----------|----------|-----------------|
| Validation run log | `validation/templates/domain-validation-run-template.md` | `validation/runs/commercial-release-COM-1-[date].md` |
| Commercial release gate checklist | `governance/release-gates.md` (commercial section) | Embedded in or linked from run log |
| Evidence packet | `validation/templates/evidence-packet-template.md` | `validation/evidence-packets/commercial-release-COM-1-[date].md` |
| External user access confirmation | No template — screenshot, log, or attestation | Part of evidence packet |
| Reviewer verdict | `validation/templates/reviewer-verdict-template.md` | `validation/reviews/commercial-release-COM-1-review-[date].md` |

All artifacts must declare Artifact Class 3 (New Execution Artifact).

---

## Founder Verification Requirements

- Founder executes the commercial release gate checklist personally
- Founder confirms monitoring/error-tracking is operational
- Founder confirms at least one external user has accessed the application
- Founder verifies core functionality from the user's perspective post-release
- Founder signs off on each MUST requirement individually in the evidence packet

---

## Release / Gate Criteria

The release gate for this pilot has two layers:
1. **The project's own release gate** — the application passes its standard release gate
2. **The commercial release overlay** — the additional commercial criteria (monitoring, support, load documentation, privacy/ToS, external user verification) are satisfied

Both layers must produce PASS for the pilot to succeed. The commercial overlay is the new element being proven.

---

## Specialist Review Requirements

None required at the current scope for the release governance itself. If the application handles personal data, a privacy review may be appropriate — but that is a data-governance concern, not a release-gate concern. The release gate includes a privacy/ToS assessment step, which is the minimum for this pilot.

---

## Promotion Criteria

Commercial Release Governance may be promoted from Untested to Validated when:

1. This pilot (or equivalent) completes with a PASS gate verdict on both the standard and commercial layers
2. All required evidence artifacts are filed, including external user access confirmation
3. Reviewer verdict is filed
4. Independent re-execution proof is on file
5. `validation/domain-matrix.md` is updated in the same commit as the reviewer verdict
6. `validation/validation-ledger.md` is updated to reflect new status and artifact links

The domain remains Untested until all conditions are met.

**Note:** A successful COM-1 proves commercial release governance was exercised once. It does not prove the governance works across all project types or at all scales. The claim boundary will be scoped to the specific pilot's context.

---

_This is a pre-execution planning document. It does not constitute evidence of validation. Filing this spec does not change the domain's current status._
