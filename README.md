# CTO Build Framework

**Companion framework and validation archive for *The CTO Build Book***

---

## Project Overview

This repository is the operational companion to [The CTO Build Book](https://github.com/yosiwizman/cto-build-framework). It contains the governance documentation, validation tracking, domain validation matrix, pilot project evidence, and simulation protocols that support the book's evidence-based development methodology.

This is an engineering governance program, not a marketing asset. Every claim in this repository is bounded by documented evidence. Every domain status reflects actual validation work, not projected capability.

## Relationship to The CTO Build Book

The CTO Build Book teaches non-technical founders how to govern AI-built software using structured scope, evidence-based verification, and release gates. The book is the narrative guide — it explains the operating model in founder language.

This repository is the operational layer. It carries:

- The full governance documentation (core loop, release gates, rollback protocol, audit separation)
- The domain validation matrix showing exactly what has been proven and what remains untested
- Pilot project documentation with evidence summaries
- Simulation protocols for testing governance under controlled conditions
- A structured roadmap for expanding validation into new domains

The book teaches you to think like a governing founder. This framework gives you the tools to act like one.

## Governance Model Overview

The CTO Build Framework is built on a single governance loop that applies at every scale:

1. **Scope** — Define what will be built with specific, testable requirements
2. **Architecture** — Approve a structural plan before building begins
3. **Build** — Execute in small, independently testable slices with checkpoints after each
4. **Verify** — Capture evidence for every requirement through founder verification
5. **Gate** — Run a structured release gate that checks all requirements against documented evidence
6. **Release** — Ship only what passes the gate with a scored, documented verdict

This loop is the same whether the project is a personal task tracker or a multi-service payment system. What changes is the number of governance layers activated — not the loop itself.

See [`/governance`](./governance/) for full documentation of each governance component.

## Evidence-Based Development Doctrine

The framework operates under a strict evidence doctrine:

- **You may claim exactly what your evidence supports. No more.**
- Every requirement is tracked through five truth states: Planned → Implemented → Tested → Proven → Honestly Claimable
- The system checking its own work (Tested) is not the same as the founder checking the system's work (Proven)
- Evidence is version-bound — proof captured against one version says nothing about a changed version
- The release gate produces a scored verdict, not a subjective judgment
- Narrow claims backed by evidence are worth more than broad claims backed by confidence

This doctrine applies to the framework itself. See [Current Validation Status](#current-validation-status) below.

## Current Validation Status

The core governance loop has been validated through two pilot projects:

| Pilot | Class | Requirements | Result | Gate |
|-------|-------|-------------|--------|------|
| Task Tracker | Standard (Class 1) | 10 MUST | 10/10 Proven | PASS |
| Contact Manager | Standard (Class 2) | 14 MUST | 14/14 Proven | PASS |

Both pilots were client-side web applications with local storage, built and released under full governance. The core loop — from natural-language request through evidence-backed release — is validated for Standard-class projects.

The governance system is designed for broader domains (backend services, authentication, payments, deployment, regulated industries). Those domains have not been field-tested. See the [Domain Validation Matrix](#domain-validation-matrix) for the full status.

## Domain Validation Matrix

| Domain | Status | Evidence | Notes |
|--------|--------|----------|-------|
| CRUD / Local-State Applications | **Validated** | Class 1 pilot: task tracker (10/10 MUST proven) | Core governance loop proven |
| Client-Side Multi-Page Apps | **Validated** | Class 2 pilot: contact manager (14/14 MUST proven) | Multi-page routing, shared state |
| Search / Filtering | **Validated** | Class 2 pilot: real-time search, category filtering | Proven within client-side scope |
| Form Validation | **Validated** | Class 2 pilot: email format validation | Client-side validation proven |
| Responsive UI | **Validated** | Both pilots: founder-verified on desktop and mobile | Cross-device verification proven |
| Authentication Systems | Untested | Doctrine exists. No project built under governance. | Domain overlay designed |
| Backend / API Services | Untested | Doctrine exists. No project built under governance. | Architecture patterns documented |
| Database Integration | Untested | Doctrine exists. No project built under governance. | Persistence layer untested beyond localStorage |
| External Integrations | Untested | No project built under governance. | Third-party API consumption untested |
| Real-Time Systems | Untested | No project built under governance. | WebSocket/SSE patterns undocumented |
| Payment Systems | Untested | Doctrine exists. No project built under governance. | PCI overlay designed, not exercised |
| Deployment Pipelines | Untested | Doctrine exists. No project built under governance. | Production deployment untested |
| CI / Merge Governance | Untested | Doctrine exists. No project built under governance. | Branch governance designed |
| Parallel Agent Swarms | Untested | Doctrine exists. No project built under governance. | Multi-agent orchestration untested |
| VoIP / Telephony Systems | Untested | No project built under governance. | No specific doctrine |
| AI / LLM Workflows | Untested | No project built under governance. | No specific doctrine |

See [`/validation`](./validation/) for detailed breakdowns of each category.

## Validation Methodology

A domain moves from **Untested** to **Validated** only when:

1. A real project in that domain has been scoped, approved, and built under full governance
2. All MUST requirements have reached **Proven** status (founder-verified with evidence on file)
3. The release gate has been executed and produced a passing verdict
4. Evidence packets are documented and available for review

**Partially Validated** means the governance mechanisms for that domain have been tested in isolation or through simulation, but no complete project has passed through the full loop.

There is no "trust me" path to validation. The proof boundary moves outward through work, not through time passing.

## Repository Structure

```
cto-build-framework/
├── README.md                          # This file
├── LICENSE                            # MIT License
├── CONTRIBUTING.md                    # Contribution and experiment policy
├── governance/
│   ├── core-loop.md                   # The six-phase governance loop
│   ├── release-gates.md               # Release gate structure and scoring
│   ├── audit-separation.md            # Why the builder cannot be the auditor
│   └── rollback-protocol.md           # Checkpoint and rollback mechanics
├── validation/
│   ├── domain-matrix.md               # Full domain validation matrix
│   ├── validated-domains.md           # Domains with full validation evidence
│   ├── partial-domains.md             # Partially validated domains
│   └── untested-domains.md            # Domains awaiting validation
├── pilots/
│   ├── task-tracker.md                # Class 1 pilot documentation
│   └── contact-manager.md            # Class 2 pilot documentation
├── simulation/
│   └── simulation-framework.md        # Simulation protocols for governance testing
├── evidence-packets/
│   └── README.md                      # Evidence packet format and submission guide
└── roadmap/
    └── validation-roadmap.md          # Staged plan for domain expansion
```

## How Validation Progress Works

The validation program follows a structured expansion path:

1. **Standard projects** are fully validated. Founders building CRUD applications, personal tools, and client-side apps can proceed with high confidence.
2. **Complex projects** (backend, APIs, databases) are next in the validation queue. The governance mechanisms exist and are documented. Field evidence is pending.
3. **Domain-Heavy projects** (payments, security, healthcare) require domain overlays and specialist review integration. The overlay system is designed but not yet exercised.
4. **Specialist projects** (regulatory certification, safety-critical systems) are the furthest from validation. They require the most governance layers and the most rigorous evidence standards.

Each successful project in a new domain extends the proof boundary. The validation roadmap in [`/roadmap`](./roadmap/) documents the specific evidence requirements for each domain.

## Contribution and Experiment Policy

This repository tracks a live validation program. Contributions are welcome under strict evidence standards.

- **Validation experiments**: If you build a project under this governance in an untested domain and it passes the release gate, you can submit an evidence packet. See [`/evidence-packets`](./evidence-packets/) for the format.
- **Governance improvements**: Proposed changes to the governance model must include rationale, affected components, and risk assessment.
- **Documentation corrections**: Factual errors, terminology inconsistencies, and broken references can be submitted as standard pull requests.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full policy.

## Roadmap for Framework Expansion

The validation roadmap is documented in [`/roadmap/validation-roadmap.md`](./roadmap/validation-roadmap.md). Key milestones:

- **Phase 1 (Current)**: Core loop validated for Standard-class client-side applications
- **Phase 2 (Next)**: Backend/API/database validation through targeted pilot projects
- **Phase 3**: Authentication, external integrations, deployment pipeline validation
- **Phase 4**: Domain-Heavy validation (payments, security, compliance) with specialist review
- **Phase 5**: Multi-session continuity, parallel execution, and advanced orchestration

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE) for details.

The CTO Build Book (the narrative guide) is a separate, commercially published work. This repository contains only the operational framework and validation documentation.
