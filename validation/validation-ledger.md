# Validation Ledger

**Canonical high-level status ledger for all domains in the CTO Build Framework.**

This file tracks where each domain stands across the full evidence chain: validation run, evidence packet, reviewer verdict, and simulation coverage. It is updated only when a corresponding artifact exists. Status labels are not updated by assertion.

For detailed domain status definitions, see [`domain-matrix.md`](./domain-matrix.md).
For artifact requirements before a status change, see [How the Matrix Updates](./domain-matrix.md#how-the-matrix-updates).

---

## How to Read This Ledger

| Column | Meaning |
|--------|---------|
| **Domain** | The capability area being tracked |
| **Current Status** | Validated / Partially Validated / Untested |
| **Last Validation Run** | Link to run log, or "None on file" |
| **Evidence Packet** | Link to formal packet, or "None on file" |
| **Reviewer Verdict** | Link to reviewer verdict file, or "None on file" |
| **Simulation Coverage** | Rollback/recovery tested in this domain — Yes / Partial / No |
| **Notes / Limits** | Known gaps, conditions, or proof-boundary limits |

**Important:** "None on file" means no canonical artifact exists in the current evidence system — no formal run log, evidence packet, or reviewer verdict has been filed in template format. For currently Validated domains, historical narrative records may exist in `pilots/` and in `validation/validated-domains.md`, but those are pre-template legacy files and are not canonical evidence sources. Canonical present-day evidence lives in `validation/evidence-packets/`, `validation/reviews/`, `validation/domain-matrix.md`, and `validation/validation-run-index.md`. All current reviewer verdicts for Validated domains are PARTIAL — independent re-execution is outstanding.

---

## Status Ledger

| Domain | Current Status | Last Validation Run | Evidence Packet | Reviewer Verdict | Simulation Coverage | Notes / Limits |
|--------|---------------|---------------------|-----------------|-----------------|--------------------|--------------:|
| CRUD / Local-State Applications | **Validated** | None on file (run pre-dates template) | [`validation/evidence-packets/task-tracker-client-side-crud.md`](./evidence-packets/task-tracker-client-side-crud.md) — filed 2026-03-16; packet incomplete (screenshots not in repo) | [`validation/reviews/crud-local-state-task-tracker-review-2026-03-16.md`](./reviews/crud-local-state-task-tracker-review-2026-03-16.md) — PARTIAL — documentation review only; human re-execution not yet on file | No | Proven for localStorage, single-page, client-side only. No backend, no server persistence. |
| Client-Side Multi-Page Apps | **Validated** | None on file (run pre-dates template) | [`validation/evidence-packets/contact-manager-client-side-multipage.md`](./evidence-packets/contact-manager-client-side-multipage.md) — filed 2026-03-16; packet incomplete (screenshots not in repo) | [`validation/reviews/client-side-multipage-contact-manager-review-2026-03-16.md`](./reviews/client-side-multipage-contact-manager-review-2026-03-16.md) — PARTIAL — documentation review only; human re-execution not yet on file | No | Proven for hash routing, shared state, multi-view apps. Client-side only. |
| Search / Filtering | **Validated** | None on file | [`validation/evidence-packets/contact-manager-search-filtering.md`](./evidence-packets/contact-manager-search-filtering.md) — filed 2026-03-16; packet incomplete (screenshots not in repo) | [`validation/reviews/search-filtering-contact-manager-review-2026-03-16.md`](./reviews/search-filtering-contact-manager-review-2026-03-16.md) — PARTIAL — documentation review only; human re-execution not yet on file | No | Real-time search and category filtering proven within Pilot 2 scope. In-memory / localStorage only. |
| Form Validation | **Validated** | None on file | [`validation/evidence-packets/contact-manager-form-validation.md`](./evidence-packets/contact-manager-form-validation.md) — filed 2026-03-16; packet incomplete (screenshots not in repo) | [`validation/reviews/form-validation-contact-manager-review-2026-03-16.md`](./reviews/form-validation-contact-manager-review-2026-03-16.md) — PARTIAL — documentation review only; human re-execution not yet on file | No | R-09 only: client-side email format validation. No server-side validation. No other field types proven. Domain label narrower than it appears. |
| Responsive UI (Desktop + Mobile) | **Validated** | None on file | [`validation/evidence-packets/responsive-ui-both-pilots.md`](./evidence-packets/responsive-ui-both-pilots.md) — filed 2026-03-16; packet incomplete (screenshots not in repo, device details not recorded) | [`validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md`](./reviews/responsive-ui-both-pilots-review-2026-03-16.md) — PARTIAL — documentation review only; device/OS/browser not on record; human re-execution on documented devices outstanding | No | Founder-verified on desktop + mobile across both pilots. Device names, OS, browser not recorded. Screenshots not filed. Breakpoints not documented. Device-detail gap most material for this domain. |
| Multi-Session Continuity | **Partially Validated** | None on file | None on file | None on file | No | Handoff protocol designed and documented. No complete multi-session project run on file. |
| Authentication / Authorization | **Partially Validated** | `validation/runs/auth-authorization-AUTH-1-2026-03-19.md` | `validation/evidence-packets/auth-authorization-AUTH-1-2026-03-19.md` | `validation/reviews/auth-authorization-AUTH-1-review-2026-03-19.md` — PARTIAL | No | AUTH-1 pilot complete. 10/10 MUST proven by Puppeteer automation with screenshots. Self-review security. Independent re-execution outstanding. Founder manual verification outstanding. |
| Backend / API / Database | **Untested** | None | None | None | No | Doctrine exists. Architecture patterns documented. No project built under governance. |
| External Integrations (Third-Party APIs) | **Untested** | None | None | None | No | No doctrine. No project built. |
| Real-Time / Event-Driven | **Untested** | None | None | None | No | No doctrine. WebSocket/SSE patterns undocumented. |
| Payments / Compliance | **Untested** | None | None | None | No | PCI overlay designed. No project built under governance. |
| Production Deployment / Runtime | **Untested** | None | None | None | No | Doctrine exists. No deployment exercised. |
| CI / Branch / Merge Governance | **Untested** | None | None | None | No | Branch governance designed. No project exercised. |
| Swarm / Parallel Execution | **Untested** | None | None | None | No | Multi-agent orchestration doctrine exists. Not exercised. |
| VoIP / Telephony | **Untested** | None | None | None | No | No doctrine. No project. |
| AI / LLM Workflows | **Untested** | None | None | None | No | No doctrine. No project. |

---

## Backlog: Formalization Work

The following work is required to bring the existing Validated domain evidence into the canonical artifact format. This is infrastructure work, not new validation work — the underlying evidence exists but has not been formalized.

| Task | Domain | Priority | Status |
|------|--------|---------|--------|
| File canonical evidence packet for CRUD / Local-State pilot | CRUD / Local-State | High | Filed (incomplete) — `validation/evidence-packets/task-tracker-client-side-crud.md` — gaps: screenshots not in repo; documentation review filed at PARTIAL |
| File canonical evidence packet for Client-Side Multi-Page pilot | Client-Side Multi-Page | High | Filed (incomplete) — `validation/evidence-packets/contact-manager-client-side-multipage.md` — gaps: screenshots not in repo; documentation review filed at PARTIAL |
| File canonical evidence packet for Search / Filtering (from Pilot 2) | Search / Filtering | High | Filed (incomplete) — `validation/evidence-packets/contact-manager-search-filtering.md` — gaps: screenshots not in repo; documentation review filed at PARTIAL |
| File canonical evidence packet for Form Validation (from Pilot 2) | Form Validation | Medium | Filed (incomplete) — `validation/evidence-packets/contact-manager-form-validation.md` — gaps: screenshot not in repo; documentation review filed at PARTIAL |
| File canonical evidence packet for Responsive UI (from both pilots) | Responsive UI | Medium | Filed (incomplete) — `validation/evidence-packets/responsive-ui-both-pilots.md` — gaps: screenshots not in repo, device names/OS/browser not recorded; documentation review filed at PARTIAL |
| Conduct and log first multi-session continuity validation run | Multi-Session Continuity | High | Not started |
| Complete independent human review of Task Tracker — re-execute software against all 10 requirements | CRUD / Local-State | Medium | Not started — documentation review filed; human re-execution outstanding |
| Complete independent human review of Contact Manager — re-execute software against all 14 requirements; reviewer must be independent of original build | Client-Side Multi-Page | Medium | Not started — documentation review filed; human re-execution outstanding |
| Complete independent human review of Contact Manager search and filtering — re-execute R-05 (search by name/company) and R-06 (filter by category) including combined simultaneous use | Search / Filtering | Medium | Not started — documentation review filed; human re-execution outstanding |
| Complete independent human review of Contact Manager email validation — re-execute R-09 only; test valid and invalid email inputs; scope remains client-side email format only | Form Validation | Medium | Not started — documentation review filed; human re-execution outstanding |
| Complete independent re-execution of responsive layout on documented devices — record device name, OS version, and browser; test both Task Tracker and Contact Manager; this domain requires environment details, not just screenshots | Responsive UI | Medium | **Automated run executed 2026-03-17** — Playwright 1.58.2 / Chromium-1208 headless; 10/10 layout checks PASS; Class 2 source / Class 3 result; automated run log filed (`validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md`); evidence packet filed (`validation/evidence-packets/responsive-ui-reconstructed-2026-03-17.md`); reviewer verdict filed PARTIAL (`validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md`); run index updated (responsive-002 Completed-PARTIAL); human re-execution protocol maintained separately (`validation/runs/responsive-ui-human-reexecution-planned.md`); **human physical device verification on real devices still outstanding** — automated run does not satisfy the "human re-execution" requirement; domain status unchanged |

---

## Ledger Change Protocol

Before updating any row in this ledger:

1. The corresponding artifact must exist and be filed in `validation/runs/`, `validation/evidence-packets/`, or `validation/reviews/`
2. The `domain-matrix.md` status must be updated in the same commit
3. The commit message must name the domain and the artifact being added
4. No status may be upgraded without a reviewer verdict on file — a PARTIAL verdict (documentation review only) is insufficient to upgrade a domain to Validated; full Validated status requires a reviewer verdict based on independent re-execution proof (see [`domain-matrix.md` — Re-Execution Requirement](./domain-matrix.md#re-execution-requirement-for-full-validation))

Do not update this ledger without an artifact. The ledger reflects what exists, not what is planned.

---

_Last updated: 2026-03-17. Updated (third pass): Separated responsive-002 automated run log from human re-execution protocol — automated run log now at `validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md`; human protocol restored and maintained separately at `validation/runs/responsive-ui-human-reexecution-planned.md`. No domain status changed. No evidence deleted or weakened. Maintained as a living document — updated only when artifacts are filed._
