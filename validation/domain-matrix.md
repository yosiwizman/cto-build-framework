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
