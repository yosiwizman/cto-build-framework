# Evidence Coverage Matrix

**Canonical claim-boundary control document for the CTO Build Framework.**

This file maps the framework's major practices and claim areas to their current evidence state. It is intended to be used before any public statement, publication draft, or README update — to ensure that what is claimed matches what has actually been proven.

It is not a marketing document. It is a control document. If a practice row says **Doctrine Only**, that practice must not be presented publicly as field-tested. If a domain row says **Untested**, that domain must not be cited as a validated use case.

This file must be read alongside `validation/domain-matrix.md` (authoritative domain status) and `validation/validation-ledger.md` (current evidence chain status).

---

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Proven** | At least one real project exercised this practice under full governance, with evidence on file. Scope boundary applies — Proven in one context does not imply Proven universally. |
| **Partially Supported** | The practice is documented in doctrine and was partially exercised, but the evidence chain is incomplete. Named gaps exist in the repo. |
| **Doctrine Only** | The practice is written and described in this repo's governance files. No real project has exercised it under full governance. Documentation is not evidence. |
| **Untested** | Neither doctrine nor field evidence exists. The practice area has not been addressed by this framework. Do not cite it. |

**Important scope note on Proven rows:** "Proven" as used here means the practice was exercised in at least one real, complete governance run. It does not mean proven universally, proven across all project types, or proven at scale. The scope boundary for each Proven row is stated explicitly.

---

## Coverage Table

### Part A — Core Governance Loop Practices

| Practice / Claim Area | Current Evidence State | Scope Boundary | Supporting Artifacts | Notes / Gaps |
|-----------------------|----------------------|----------------|---------------------|-------------|
| Six-phase governance loop (Scope → Architecture → Build → Verify → Gate → Release) | **Proven** | Standard-class client-side web applications only — two pilots | `pilots/task-tracker.md`, `pilots/contact-manager.md`, `validation/evidence-packets/task-tracker-client-side-crud.md`, `validation/evidence-packets/contact-manager-client-side-multipage.md` | Both pilot builds completed all six phases. Loop not yet proven for backend, server-rendered, or domain-heavy projects. |
| Slice-based delivery / micro-slice execution | **Proven** | Standard-class client-side builds; both pilots used it | `pilots/task-tracker.md` (10 slices, no escalation), `pilots/contact-manager.md` (14+ requirements, no escalation) | Happy-path slice execution confirmed. All slices in both pilots completed without requiring a failed-slice rollback. |
| Checkpoint system (save verified state after each slice) | **Partially Supported** | Both pilots documented post-slice checkpoints | `pilots/task-tracker.md`, `pilots/contact-manager.md` | Checkpoints created and used in both pilots. However, no pilot triggered a checkpoint recovery — both runs were clean. The checkpoint-recovery path is not on record as having been exercised. |
| Rollback under failure / escalation ladder (Levels 1-3) | **Doctrine Only** | Documented in governance files — not triggered in any pilot | `governance/rollback-protocol.md` | Both pilots completed with zero scope drift and no escalation events requiring founder intervention. The rollback-under-failure path was never triggered. Doctrine is written; execution under failure is not on record. |
| Five truth-state evidence progression (Planned → Implemented → Tested → Proven → Honestly Claimable) | **Proven** | Both pilots tracked all MUST requirements through this sequence | `pilots/task-tracker.md` (10/10 MUST at Proven), `pilots/contact-manager.md` (14/14 MUST at Proven) | Progression was exercised for all MUST requirements in both pilots. NICE requirements and partial-progress requirements were not exercised. |
| Founder verification as a distinct step from AI self-testing (audit separation) | **Proven** | Both pilots required and recorded founder verification before gate | `governance/audit-separation.md`, `pilots/task-tracker.md`, `pilots/contact-manager.md` | Founder independently verified all MUST requirements. Evidence captured (screenshots, test records noted). Original verification artifacts not formally filed in current evidence-packet format; current reviewer verdicts are PARTIAL. |
| Personal Production Gate (scored, structured verdict) | **Proven** | Both pilots ran the gate with scored verdicts | `pilots/task-tracker.md` (Confidence 28/35, Sufficiency 16/20, PASS), `pilots/contact-manager.md` (Confidence 27/35, Sufficiency 15/20, PASS) | Gate executed and passed in both pilots. Gate records are in narrative pilot files — not in formal template format. |
| Commercial Release Gate | **Doctrine Only** | Documented; explicitly stated as not field-tested | `governance/release-gates.md` | The commercial gate is described in `release-gates.md` with a note: "This gate exists in the framework but has not been field-tested." Do not present this gate as proven. |
| Scope drift prevention / out-of-scope enforcement | **Proven** | Both pilots had zero scope drift | `pilots/task-tracker.md` ("Zero scope drift"), `pilots/contact-manager.md` ("15 explicitly excluded features remained excluded") | Scope boundary held in both pilots. Only tested in single-session builds with a single operator — multi-session or multi-operator scope enforcement not yet tested. |

---

### Part B — Proof and Evidence Governance

| Practice / Claim Area | Current Evidence State | Scope Boundary | Supporting Artifacts | Notes / Gaps |
|-----------------------|----------------------|----------------|---------------------|-------------|
| Proof-boundary doctrine (claim only what evidence supports) | **Proven** (as an operational practice) | Applied throughout this repo | `CLAUDE.md`, `validation/domain-matrix.md`, all reviewer verdicts | This repo consistently applies the doctrine — PARTIAL verdicts, named gaps, no silent upgrades. Operationally proven as a governance practice. Its effectiveness in external contexts is not yet evidenced. |
| Artifact classification system (Class 1 / Class 2 / Class 3) | **Partially Supported** | System documented and applied to responsive-002 | `validation/domain-matrix.md` (Artifact Classification section), `validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md`, `validation/evidence-packets/responsive-ui-reconstructed-2026-03-17.md` | Classification framework is complete and has been applied to at least one run. Original pilots predate this system and were not retroactively reclassified under it. Gap: system has not been applied to a full domain validation cycle from scratch. |
| Independent re-execution requirement (human operator, live execution, physical devices) | **Doctrine Only** | Documented; no domain has completed it | `validation/domain-matrix.md` (Re-Execution Requirement section) | The requirement is documented clearly. An automated Playwright run (responsive-002) produced Class 3 evidence but does not satisfy this requirement — it was not human, not on physical devices. All current domain reviewer verdicts are PARTIAL because independent re-execution is outstanding. |
| Validation run index / evidence infrastructure (runs, evidence-packets, reviews) | **Partially Supported** | Infrastructure exists and is operational | `validation/validation-run-index.md`, `validation/evidence-packets/`, `validation/reviews/` | All templates and infrastructure are in place. Current evidence packets for validated domains are incomplete (screenshots not filed, device details not recorded). All reviewer verdicts for validated domains are PARTIAL. Infrastructure is functional but not yet populated with complete, class-compliant artifacts. |
| Evidence version-binding (proof against one version, not another) | **Proven** (as a stated rule) | Applied in both pilots | `governance/core-loop.md` (Loop Invariants) | Stated and applied as a rule. Both pilot evidence was captured at defined git states. Formal commit-hash tracking is present in responsive-002 run log; original pilots lack this level of traceability. |

---

### Part C — LLM Operating Discipline

| Practice / Claim Area | Current Evidence State | Scope Boundary | Supporting Artifacts | Notes / Gaps |
|-----------------------|----------------------|----------------|---------------------|-------------|
| Structured work-order prompting (scope, constraints, deliverables, acceptance criteria) | **Partially Supported** | Applied in both pilots; no formal prompt records on file | `governance/llm-operating-discipline.md` (Section 2) | The discipline is documented and was applied during the pilots. No formal prompt-log artifacts exist in the repo. Evidence is the fact that the pilots completed successfully under structured scope documents. |
| Micro-slice rhythm — one slice, verify green, checkpoint, next slice | **Proven** | Both pilots — all slices verified before proceeding | `pilots/task-tracker.md`, `pilots/contact-manager.md` | Applied in practice. Documented in pilot build summaries. Happy-path only (no failed-slice recovery on record). |
| Environment hygiene (clean git state, kill stale servers, no leftover artifacts) | **Partially Supported** | Applied in practice; no formal environment-hygiene logs | `governance/llm-operating-discipline.md` (Section 4) | Doctrine is documented with a pre-session checklist. Pilots were conducted in controlled conditions. No formal environment hygiene records were filed as artifacts. |
| Scout passes and mapper passes before modification | **Partially Supported** | Applied informally; no formal scout logs | `governance/llm-operating-discipline.md` (Section 6) | Doctrine is documented. Both pilots used read-before-write practices. No formal scout-pass logs are filed as artifacts. Gap: scout pass records would strengthen this claim. |
| Handoff documents / context compression across sessions | **Partially Supported** | Doctrine documented; not triggered in either pilot | `governance/llm-operating-discipline.md` (Section 6) | Both pilots were completed in single sessions, so no inter-session handoff was required or exercised. The handoff protocol is documented and tested for single-to-single transfers; actual multi-session recovery is not on record. |
| Isolated scout environments (disposable sandbox before governed build) | **Doctrine Only** | Documented in Section 7 of LLM discipline doc; not evidenced | `governance/llm-operating-discipline.md` (Section 7) | This practice is fully described. No pilot produced a scout environment artifact or used an isolated sandbox as a documented step. Do not present as a proven practice. |
| Founder-as-orchestrator / non-coder governance model | **Partially Supported** | Exercised in both pilots; framework designer as operator | `governance/llm-operating-discipline.md` (Section 9), `pilots/task-tracker.md`, `pilots/contact-manager.md` | The orchestration model works when followed by someone who understands it. Both pilots were conducted by the framework designer, not by an independent non-coder founder new to the framework. Independent external operator verification is outstanding. |
| Session decay management (fresh sessions, clean context) | **Partially Supported** | Applied in practice; not formally documented per pilot | `governance/llm-operating-discipline.md` (Section 1, Section 6) | Doctrine is clear on this failure mode. Both pilots completed in single sessions — session decay was not a factor. The doctrine's value is most relevant to multi-session projects, which have not yet been formally exercised. |

---

### Part D — Domain Application Evidence

| Practice / Claim Area | Current Evidence State | Scope Boundary | Supporting Artifacts | Notes / Gaps |
|-----------------------|----------------------|----------------|---------------------|-------------|
| CRUD / Local-State Applications | **Proven** | Single-page; localStorage only; no backend; no server | `pilots/task-tracker.md`, `validation/evidence-packets/task-tracker-client-side-crud.md`, `validation/reviews/crud-local-state-task-tracker-review-2026-03-16.md` — PARTIAL | 10/10 MUST at Proven. Gate PASS. Evidence packet filed (incomplete — screenshots not in repo). Reviewer verdict PARTIAL (independent re-execution outstanding). |
| Client-Side Multi-Page Applications | **Proven** | Hash routing; client-side state only; no backend; no server | `pilots/contact-manager.md`, `validation/evidence-packets/contact-manager-client-side-multipage.md`, `validation/reviews/client-side-multipage-contact-manager-review-2026-03-16.md` — PARTIAL | 14/14 MUST at Proven. Gate PASS. Evidence packet filed (incomplete — screenshots not in repo). Reviewer verdict PARTIAL (independent re-execution outstanding). |
| Search / Filtering | **Proven** (narrow scope) | In-memory/localStorage only; name + company search; single category filter; Pilot 2 only | `validation/evidence-packets/contact-manager-search-filtering.md`, `validation/reviews/search-filtering-contact-manager-review-2026-03-16.md` — PARTIAL | R-05 (search by name/company) and R-06 (filter by category) Proven. Combined search + filter behavior verified. Server-side search, faceted search, and pagination not tested. |
| Form Validation | **Proven** (extremely narrow scope) | Client-side email format validation only (R-09 in Pilot 2) — nothing else | `validation/evidence-packets/contact-manager-form-validation.md`, `validation/reviews/form-validation-contact-manager-review-2026-03-16.md` — PARTIAL | The domain label "Form Validation" is broader than what was proven. Only one rule was tested: email format on one field in one form. No other field types, no required-field enforcement beyond email, no server-side validation proven. |
| Responsive UI (Desktop + Mobile) | **Partially Supported** | Both pilots; client-side apps; device details not recorded | `validation/evidence-packets/responsive-ui-both-pilots.md`, `validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md` — PARTIAL; `validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md` (Class 2/3, automated only), `validation/evidence-packets/responsive-ui-reconstructed-2026-03-17.md` | Founder-verified on desktop + mobile in both pilots. Device names, OS versions, and browser versions were never recorded. Screenshots not filed in repo. Automated Playwright run (responsive-002) confirmed reconstructed apps render without overflow but used headless browser and simulated mobile, not physical devices. Reviewer verdicts PARTIAL. Claim is weaker than the "Validated" status label implies for public framing purposes. |
| Multi-Session Continuity | **Partially Supported** | Doctrine designed; handoff protocol documented | `validation/partial-domains.md`, `validation/domain-matrix.md` | Both pilots completed in single sessions. No project has exercised the handoff protocol across a session break. Doctrine exists and is internally consistent. Not field-tested. |
| Backend / API / Database | **Doctrine Only** | Architecture patterns documented; no project built | `validation/untested-domains.md`, `validation/domain-matrix.md` | Domain overlay and architecture patterns documented. No project built under governance. Not proven. Not partially proven. Doctrine only. |
| Authentication / Authorization | **Doctrine Only** | Domain overlay designed; no project built | `validation/untested-domains.md`, `validation/domain-matrix.md` | Session management, RBAC, OAuth patterns documented. No project built under governance. |
| External Integrations (Third-Party APIs) | **Untested** | No doctrine; no project | `validation/domain-matrix.md` | No governance design exists for this area. Cannot be cited. |
| Real-Time / Event-Driven Systems | **Untested** | No doctrine; no project | `validation/domain-matrix.md` | WebSocket/SSE patterns not documented. No project built. Cannot be cited. |
| Payment Systems / Compliance (PCI) | **Doctrine Only** | PCI overlay designed; no project built | `validation/untested-domains.md`, `validation/domain-matrix.md` | PCI overlay is documented. Has not been exercised. Do not present payment governance as proven. |
| Production Deployment / Runtime | **Doctrine Only** | Deployment governance designed; no deployment exercised | `validation/untested-domains.md`, `validation/domain-matrix.md` | All pilots were client-side apps with no server and no production deployment. Production runtime governance exists as doctrine only. |
| CI / Branch / Merge Governance | **Doctrine Only** | Branch governance designed; no project exercised it | `validation/untested-domains.md`, `validation/domain-matrix.md` | This repo uses GitHub but its CI governance has not been exercised as a governed build practice in any pilot project. |
| Parallel Agent / Swarm Execution | **Doctrine Only** | Multi-agent orchestration doctrine; no project built | `validation/untested-domains.md`, `validation/domain-matrix.md` | Doctrine describes conflict resolution, state synchronization, and parallel task assignment. Nothing exercised. |
| VoIP / Telephony Systems | **Untested** | No doctrine; no project | `validation/domain-matrix.md` | No governance design exists for this area. Cannot be cited. |
| AI / LLM Workflow Integration | **Untested** | No doctrine; no project | `validation/domain-matrix.md` | No governance design for LLM-in-the-loop applications, prompt management, or output validation. Cannot be cited. |

---

## Interpretation Notes

**"Proven" is narrow.** When a row says Proven, it means: a real governance run executed this practice or confirmed this domain, with evidence artifacts on file. It does not mean universally applicable, proven at scale, proven with multiple independent operators, or proven across project types. Every Proven row has a scope boundary. Read it.

**Reconstructed-artifact runs do not upgrade original-pilot confidence.** The responsive-002 Playwright run (`validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md`) produced Class 3 evidence from Class 2 (reconstructed) source files. It does not confirm that the original pilot deliverables behave the same way, and it does not satisfy the independent re-execution requirement in `validation/domain-matrix.md`. It is useful Class 3 evidence for the reconstructed apps. It is not additional proof of the original pilots.

**Doctrine can exist ahead of evidence.** Several rows say Doctrine Only. This is not a failure — it means the framework has been designed for those areas and the governance mechanisms are ready to exercise. It means: do not claim field-tested capability for them yet. The work to move a row from Doctrine Only to Proven is a structured validation run, not a documentation update.

**All current reviewer verdicts for validated domains are PARTIAL.** The five domains listed as Validated in `validation/domain-matrix.md` all have PARTIAL reviewer verdicts on file. This means the evidence was reviewed against what exists, and what exists is not complete enough for a PASS verdict. Independent re-execution on physical devices with recorded environment details is the outstanding requirement for all of them.

**Publication and public framing must follow this matrix, not ambition.** If a claim cannot be supported by a Proven or Partially Supported row in this table with a clear scope boundary, it must not appear in public-facing materials without explicit qualification.

---

## Priority Gaps

These are the highest-priority evidence gaps revealed by this matrix, in order of publication-risk impact:

| # | Gap | Risk | Path to Close |
|---|-----|------|--------------|
| 1 | **Responsive UI** — device details, OS, browser, and screenshots not on file; reviewer verdict PARTIAL | High — domain labeled Validated but evidence is weaker than the label implies for public framing | Human operator: open both apps on real desktop and real mobile device, record device/OS/browser, file screenshots per `validation/runs/responsive-ui-human-reexecution-planned.md` |
| 2 | **Independent re-execution on physical devices (all validated domains)** — no domain has a complete human re-execution artifact trail | High — PARTIAL verdicts for all five Validated domains; full Validated status (per current doctrine) requires this | Execute re-execution runs per the re-execution requirement in `validation/domain-matrix.md`; file run logs, evidence packets, and verdicts for each domain |
| 3 | **Rollback under failure** — neither pilot triggered an escalation or rollback; doctrine untested in adversarial conditions | Medium — a live demo of recovery-under-failure would substantially strengthen the claim that checkpoints and rollback actually work | Deliberately trigger a failure during a governed build exercise and document the recovery path as a Class 3 validation run |
| 4 | **Founder-as-orchestrator with an independent non-coder operator** — both pilots were built by the framework designer | Medium — the core audience claim (non-coder founders can govern AI-built software) has not been independently verified with an external operator | Conduct a governed pilot with an independent non-coder founder who is new to the framework; document the process and outcome |
| 5 | **Multi-session continuity** — handoff protocol designed and documented but never exercised in a project that required session breaks | Medium — the handoff claim cannot be evidenced from single-session builds | Execute a planned multi-session governed build that uses the handoff protocol across at least one session break |
| 6 | **Backend / API domain** — doctrine exists but no field evidence | Medium — expanding the validated range is the next stated roadmap priority | Execute a Phase 2 pilot project with a backend API under full governance |
| 7 | **Form Validation label breadth** — the label "Form Validation" implies broader coverage than one email format rule | Low-medium — risk is overstating what was proven | Either narrow the public label to "Email Format Validation (client-side)" or expand through additional pilots |
| 8 | **Evidence packet screenshots** — original pilot screenshots not filed in repo; current packets marked incomplete | Low — acknowledged gap that does not invalidate the pilot results | File screenshots to repo if recoverable; note explicitly when they are not |

---

_Created 2026-03-17. Maps current repo evidence state only — does not project future capability. Update this file when a new validated domain run is completed and its artifacts are filed. This file does not replace `validation/domain-matrix.md` (authoritative status) or `validation/validation-ledger.md` (evidence chain tracking) — it synthesizes across both for publication-risk audit purposes._
