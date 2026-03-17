# Domain Validation Matrix

This document tracks the validation status of the CTO Build Framework across all identified software domains. A domain is marked **Validated** only when at least one real project in that domain has completed the full governance cycle with all MUST requirements at Proven and evidence on file.

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Validated** | At least one project completed the full governance loop with all MUST requirements Proven |
| **Partially Validated** | Governance mechanisms tested in isolation or simulation, but no complete project through the full loop |
| **Untested** | Doctrine may exist, but no project or simulation has exercised the governance in this domain |

## Full Matrix

| Domain | Status | Evidence Source | Notes |
|--------|--------|----------------|-------|
| CRUD / Local-State Applications | **Validated** | Class 1 pilot: task tracker (10/10 MUST) | Core loop proven |
| Client-Side Multi-Page Apps | **Validated** | Class 2 pilot: contact manager (14/14 MUST) | Routing, shared state, multi-page navigation |
| Search / Filtering | **Validated** | Class 2 pilot | Real-time search, category filtering proven |
| Form Validation | **Validated** | Class 2 pilot | Email format validation proven |
| Responsive UI (Desktop + Mobile) | **Validated** | Both pilots | Founder-verified on desktop and mobile |
| Multi-Session Continuity | Partially Validated | Doctrine tested; both pilots completed in single sessions | Handoff protocol designed, not fully exercised |
| Authentication / Authorization | Untested | Doctrine exists | Domain overlay designed, no project built |
| Backend / API / Database | Untested | Doctrine exists | Architecture patterns documented |
| External Integrations (Third-Party APIs) | Untested | No doctrine | API consumption untested |
| Real-Time / Event-Driven | Untested | No doctrine | WebSocket/SSE undocumented |
| Payments / Compliance | Untested | Doctrine exists | PCI overlay designed |
| Production Deployment / Runtime | Untested | Doctrine exists | No deployment exercised |
| CI / Branch / Merge Governance | Untested | Doctrine exists | Branch governance designed |
| Swarm / Parallel Execution | Untested | Doctrine exists | Multi-agent orchestration untested |
| VoIP / Telephony | Untested | No doctrine | No specific governance designed |
| AI Integration / LLM Workflows | Untested | No doctrine | No specific governance designed |

## How the Matrix Updates

When a project in an untested domain passes through the full governance loop:
1. The evidence packet is submitted and reviewed
2. The domain status is updated from Untested to Validated (or Partially Validated if conditions apply)
3. The validated-domains.md document is updated with the evidence summary
4. The proof boundary in the README is updated accordingly

**Required artifact trail for any status change:**

| Artifact | Required | Template |
|---------|---------|---------|
| Validation run log | Yes | `validation/templates/domain-validation-run-template.md` |
| Evidence packet | Yes | `validation/templates/evidence-packet-template.md` |
| Reviewer verdict | Yes (Proven status requires independent review) | `validation/templates/reviewer-verdict-template.md` |
| Simulation log | Required for Partially Validated or above in recovery-sensitive domains | `validation/templates/simulation-log-template.md` |

No status change is accepted without the evidence packet and reviewer verdict filed in `validation/evidence-packets/` and `validation/reviews/` respectively.

See the high-level status ledger at [`validation-ledger.md`](./validation-ledger.md) for current state across all domains including artifact filing status.

---

## Artifact Classification

All artifacts associated with this validation program fall into exactly one of three classes. Classes must not be mixed in validation claims.

### Class 1 — Original Pilot Artifacts

**Definition:** Files, logs, screenshots, and records produced during the original validated pilot runs at the time of execution.

**Validation status:** Eligible to support validation claims.

**Requirements:**
- Must have an execution trace, contemporaneous log, or founder verification record linking the artifact to a specific run
- Must be filed in `validation/evidence-packets/` or `validation/runs/` with a dated reference
- Missing original artifacts must be noted as gaps in the evidence packet — they do not invalidate the claim but reduce audit strength

**Examples:** Original Task Tracker HTML file as delivered, original Contact Manager HTML file as delivered, original gate records, original founder verification screenshots.

---

### Class 2 — Reconstructed Artifacts

**Definition:** Files generated later from documented requirements, not produced during the original pilot run.

**Validation status:** NOT valid proof of original execution. Cannot be used to support, confirm, or upgrade existing validation claims about original pilot success.

**Allowed uses:**
- UI demonstration and stakeholder communication
- Secondary automated testing, provided the run is clearly labeled as a reconstructed run in all filed artifacts
- Responsive layout testing via Playwright or similar tools, provided results are filed as a separate reconstructed evidence packet — not as a continuation of the original pilot evidence chain

**Explicit rule:** Reconstructed artifacts MUST NOT be used to fill artifact gaps in original evidence packets as if they were produced during the original pilot. A screenshot captured from a reconstructed build does not close the screenshot gap in `validation/evidence-packets/responsive-ui-both-pilots.md`.

**Location in this repo:** `reconstructed-apps/` — see `reconstructed-apps/README.md` for full classification notice.

---

### Class 3 — Future Validation Runs

**Definition:** Any new execution — human or automated — that attempts to validate additional domains or re-run existing pilots after the original pilot period.

**Validation status:** Eligible to produce new evidence, provided the full artifact trail is completed independently.

**Requirements:**
- Must produce a new, independently filed validation run log (`validation/runs/`)
- Must produce a new evidence packet (`validation/evidence-packets/`) explicitly dated and scoped to the new run
- Must not be appended to or merged with original pilot evidence packets — must stand alone
- Results from a Class 3 run using Class 2 (reconstructed) artifacts must clearly identify the artifact class in the run log and evidence packet

---

### Non-Negotiable Rules

| Rule | Rationale |
|------|-----------|
| No mixing of artifact classes in a single validation claim | Mixed-class claims cannot be evaluated — the provenance boundary collapses |
| Reconstructed artifacts cannot upgrade domain confidence | A generated file is not a historical record of what was built and verified |
| All validation claims must trace to Class 1 or Class 3 execution evidence | Documentation alone is not evidence; "designed-for" is not "proven-in" |
| If original artifacts are missing, status remains as-is with acknowledged gaps | Status is not retroactively degraded by absence of artifacts, but gaps must be named |
| Reconstructed artifacts used in testing must be labeled in all filed run artifacts | Prevents silent drift from "reconstructed run" to "original pilot confirmation" |

---

### Cross-Reference: Reconstructed Apps

The directory `reconstructed-apps/` contains Class 2 artifacts only. It is intentionally separated from `validation/` to prevent conflation with the original pilot deliverables. Nothing in `reconstructed-apps/` may be cited as original pilot evidence without a Class 3 run wrapper that explicitly names the source as reconstructed.
