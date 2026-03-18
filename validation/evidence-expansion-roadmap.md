# Evidence Expansion Roadmap

**Type:** Governance artifact — future validation planning

**Purpose:** Defines how the CTO Build Framework can expand its evidence base after publication. This file governs post-publication validation work only. It does not change any current claim boundary, any current domain status, or any publication-readiness decision.

**Date:** 2026-03-18
**Repo:** https://github.com/yosiwizman/cto-build-framework

---

## 1. Purpose

This file is for future use. It answers the question: after the book is published, how does the framework grow its evidence base honestly?

**What this file does:**
- Prioritizes validation campaigns for the domains not yet proven
- Defines minimum evidence required before any claim can widen
- States what stays out of bounds until that evidence exists
- Provides a concrete order and rationale for the next three validation efforts

**What this file does not do:**
- Change any domain status — no domain moves without a filed artifact trail
- Widen any current claim boundary
- Supersede or modify `validation/release-readiness-decision.md`
- Replace `validation/domain-matrix.md` as the authoritative domain status source

Current claim boundaries remain unchanged. This file governs how they expand, not whether they are already expanded.

---

## 2. Current Baseline

As of 2026-03-18, the framework's validated range is narrow. This is an accurate and defensible position, not a weakness.

### Validated domains (5) — all carry PARTIAL reviewer verdicts

All five were exercised in Pilot 1 (task tracker) and/or Pilot 2 (contact manager). All five have PARTIAL reviewer verdicts on file because independent re-execution is outstanding for each. The evidence is real. The gaps in the evidence chain are documented.

| Domain | Scope Limit |
|--------|-------------|
| CRUD / Local-State Applications | localStorage; no backend; no server persistence |
| Client-Side Multi-Page Apps | Hash routing; client-side state only; no backend |
| Search / Filtering | Pilot 2 contact manager only; in-memory/localStorage; name + company search; single category filter; server-side search and pagination not tested |
| Form Validation | Client-side email format validation only — one field, one rule; no server-side validation tested |
| Responsive UI (Desktop + Mobile) | Founder-verified; device names, OS, and browser not recorded; physical device re-execution outstanding |

### Partially validated (1)

| Domain | Gap |
|--------|-----|
| Multi-Session Continuity | Handoff protocol designed and documented; no complete multi-session project run on file |

### Untested — doctrine exists, no field evidence (6)

Authentication / Authorization, Backend / API / Database, Payments / Compliance, Production Deployment / Runtime, CI / Branch / Merge Governance, Swarm / Parallel Execution.

### Untested — no doctrine, no field evidence (4)

External Integrations (Third-Party APIs), Real-Time / Event-Driven Systems, VoIP / Telephony, AI / LLM Workflow Integration.

---

## 3. Roadmap Principles

These principles govern all future evidence expansion. They are not aspirational — they are constraints.

### Proof before promotion

No domain may be promoted in any public-facing material — README, book edition, marketing copy, announcement — until the corresponding evidence artifacts are filed in this repo. Filing precedes claiming, always.

### No domain widening by analogy

Proving a capability in one narrow context does not validate the broader label. "Email format validation proven" does not validate "form validation generally." "In-memory search proven" does not validate "server-side search." Expansion must be proven, not inferred.

### Tool-based verification first where applicable

Where automated tools can check a behavior — Playwright, CI, browser automation, screenshot capture — they run first. Human review of UI behavior is a fallback, not a default. See `governance/ui-validation-protocol.md` for the full hierarchy.

### Human review only where tool proof is insufficient

Physical-device claims, named OS/browser records, accessibility evaluation, and multi-session governance flows require human verification. Automation cannot substitute for these. Where human review is triggered, it must produce a documented record: what was reviewed, by whom, on what environment, with what verdict.

### One bounded domain at a time

Validation campaigns are sequential, not parallel. Running multiple unfinished domain campaigns simultaneously fragments the evidence record, creates cross-contamination risk between artifact trails, and reduces quality of each. Complete one campaign to a filed reviewer verdict before beginning the next.

---

## 4. Priority Validation Queue

Ranked by leverage and sequencing logic: completing existing partial work before opening new domains, and building from client-side outward toward infrastructure.

| Priority | Domain | Current State | Why It Matters | Minimum Evidence Needed Before Any Claim Upgrade | Likely Proof Method | Claim Boundary Until Then |
|----------|--------|---------------|----------------|--------------------------------------------------|---------------------|--------------------------|
| 1 | Responsive UI — physical device re-execution | Validated (PARTIAL) | Closes the most visible gap in the existing evidence record; device names, OS, and browser are required for any "verified on real devices" claim | Human operator executes both apps on real desktop and real mobile device; records exact device, OS version, and browser version; files screenshots, run log, and reviewer verdict per `validation/templates/` | Human re-execution per `validation/runs/responsive-ui-human-reexecution-planned.md` | Cannot claim "verified on a named device" — physical device re-execution outstanding |
| 2 | Multi-Session Continuity | Partially Validated | Converts a documented gap into a filed result; enables honest claim that the handoff protocol has been exercised in practice | At least one complete project run that spans a real session break; handoff protocol exercised at the break; evidence packet, run log, and reviewer verdict filed | Governed build with a planned session break; human founder operates as orchestrator across sessions | Cannot claim multi-session continuity is field-tested; "Partially Validated" must not be presented as Validated |
| 3 | Independent re-execution — all 5 Validated domains | Validated (PARTIAL) | Closes the PARTIAL verdict gap for all five domains; the only outstanding requirement for full reviewer verdicts under current doctrine | A party other than the original build operator re-executes each domain against its original MUST requirements; produces run log, evidence packet, and reviewer verdict independently for each | Human re-execution run per `validation/templates/domain-validation-run-template.md`; each domain is a separate, independent run | All five carry PARTIAL verdicts; "Validated" in current materials acknowledges this gap |
| 4 | Backend / API / Database | Untested | The most natural next expansion of the framework's validated range; doctrine exists; a backend pilot would cover the largest unvalidated category of production software | At least one project built under full governance with a real backend API and database; all MUST requirements at Proven; run log, evidence packet, and PASS reviewer verdict filed | Phase 2 governed pilot with a backend-API project; full six-phase governance loop | Cannot claim backend, API, or database work is validated, proven, or field-tested |
| 5 | Authentication / Authorization | Untested | Auth is present in nearly every real-world application; proving it expands the framework's applicability from frontend-only to full-stack applications | At least one project under full governance that implements session management and access control; MUST requirements covering auth flows at Proven; filed artifacts | Governed pilot where auth is a MUST requirement, not a side feature; run log, evidence packet, reviewer verdict | Cannot claim auth or session management is governed, validated, or safe under this framework |
| 6 | Production Deployment / Runtime | Untested | Client-side apps running from a file system or CDN are fundamentally different from apps with a running server; deployment governance is a distinct, unproven capability | At least one governed build that includes a real production deployment; deployment gate exercised; run log, evidence packet, and reviewer verdict filed | Governed pilot with a backend project that deploys to a real production environment | Cannot claim production deployment governance is field-tested; all current pilots were client-side only with no production server |
| 7 | CI / Branch / Merge Governance | Untested | Branch governance doctrine exists; demonstrating it in a governed project closes the gap between "designed" and "exercised" | A governed project that uses the branch governance protocol across at least one PR cycle; CI run results filed as part of the evidence record | Governed pilot project with active CI and a documented PR/merge cycle | Cannot claim CI or branch governance has been field-exercised in a production context |
| 8 | Payments / Compliance (PCI) | Untested | PCI doctrine exists; a payments project would validate the most compliance-sensitive domain on the roadmap | At least one project that implements a real payment flow under governance; PCI overlay exercised; run log, evidence packet, and reviewer verdict filed | Governed pilot with a real payment integration (Stripe or equivalent); PCI scope explicitly bounded in MUST requirements | Cannot claim payment or PCI governance is field-tested; the PCI overlay is doctrine only |
| 9 | Real-Time / Event-Driven Systems | Untested | No doctrine exists; WebSocket/SSE patterns not documented; this domain requires doctrine creation before validation can begin | Doctrine creation first (domain overlay); then at least one governed project using real-time event patterns; evidence packet and reviewer verdict filed | Two-phase: write domain overlay first; then govern a real-time pilot project | Cannot be cited; no governance design exists |
| 10 | AI / LLM Workflow Integration | Untested | No doctrine exists; governing LLM-in-the-loop applications is a distinct and growing use case; requires doctrine before field evidence | Doctrine creation first (domain overlay for prompt management, output validation, and LLM governance within a product); then at least one governed project using LLM integration; evidence artifacts filed | Two-phase: write domain overlay first; then govern a pilot project with LLM integration as a MUST feature | Cannot be cited; no governance design exists |

---

## 5. Suggested Validation Order

The correct sequencing is: **close existing gaps first, then expand to new domains**.

**Recommended order:**

1. Responsive UI physical device re-execution (Priority 1)
2. Multi-Session Continuity (Priority 2)
3. Independent re-execution for all 5 Validated domains (Priority 3)
4. Backend / API / Database pilot (Priority 4)
5. Authentication / Authorization pilot — combined with or following the Backend pilot, since auth is almost always part of a real backend project (Priority 5)
6. Production Deployment (Priority 6) — naturally follows a backend pilot; a backend project without deployment is incomplete
7. CI / Branch / Merge Governance (Priority 7) — a natural addition to any backend or deployment pilot
8. Payments / Compliance (Priority 8) — requires its own dedicated project due to PCI scope complexity
9. Real-Time / Event-Driven (Priority 9) — requires doctrine creation before field validation
10. AI / LLM Workflow Integration (Priority 10) — requires doctrine creation before field validation

**Why this order is safest and highest leverage:**

Starting with Priorities 1–3 closes gaps in the existing evidence record before claiming new territory. It strengthens the foundation that the book's claims are built on. Priorities 4–7 extend the validated range in a logical sequence — client-side to backend, then backend to deployment, then deployment to CI — each one building on the prior. Priorities 8–10 address specialized domains that require either significant compliance infrastructure (PCI) or doctrine work that does not yet exist (real-time, AI/LLM).

Attempting Priorities 4–10 before closing Priorities 1–3 would create a situation where new domain claims are made on a foundation that still has documented gaps. That is not the order in which to build credibility.

---

## 6. First Three Recommended Validation Campaigns

### Campaign 1 — Responsive UI Physical Device Re-Execution

**Campaign goal:** Close the device-detail gap in the Responsive UI domain. File a human re-execution record that names the exact device, OS version, and browser version used.

**Minimum artifact set:**
- Completed `validation/runs/responsive-ui-human-reexecution-planned.md` (the protocol is already filed — execute it)
- New evidence packet: `validation/evidence-packets/responsive-ui-human-reexecution-[date].md`
- Screenshots taken at key assertion points on both desktop and real mobile device, stored in `screenshots/`
- Reviewer verdict: `validation/reviews/responsive-ui-human-reexecution-review-[date].md`

**Required verification mode:** Human operator on physical hardware. Device name, OS version, and browser version must be recorded in the run log and evidence packet. A Playwright or headless run does not satisfy this campaign. The gap is specifically that no physical device record exists.

**What counts as success:**
- Both apps (task tracker and contact manager) verified on a named desktop (device, OS, browser) and a named mobile device (device, OS, browser)
- All layout breakpoints confirmed without overflow on both
- Screenshots filed for each device state
- Reviewer verdict upgraded from PARTIAL to PASS for the physical device component

**What still could NOT be claimed even after success:**
- That all possible device/OS/browser combinations have been tested — the record covers the specific devices used
- That the framework governs any domain beyond the five currently Validated
- That independent re-execution (a different operator) has been completed — this campaign is founder verification of physical devices, not independent operator verification

---

### Campaign 2 — Multi-Session Continuity Validation

**Campaign goal:** Produce the first complete multi-session project run on file. Exercise the handoff protocol across a real session break with a governed project.

**Minimum artifact set:**
- Validation run log: `validation/runs/multi-session-continuity-[date].md` — documents session 1 state, handoff artifact content, and session 2 continuation
- Handoff document: the actual handoff artifact produced at the session break, filed in the run log
- Evidence packet: `validation/evidence-packets/multi-session-continuity-[date].md`
- Reviewer verdict: `validation/reviews/multi-session-continuity-review-[date].md`

**Required verification mode:** Human founder operating as orchestrator across two sessions, with a real session break between them. The handoff protocol in `governance/llm-operating-discipline.md` Section 6 must be followed. The session break must be real — not a simulated handoff in a single session.

**What counts as success:**
- A project with at least 6 MUST requirements reaches Proven in session 1
- Session 1 ends with a filed handoff document
- Session 2 begins by reading the handoff — not from conversation memory
- Remaining requirements reach Proven in session 2
- Release gate executed at the end of session 2 with a PASS verdict
- No requirements were lost, duplicated, or contradicted across the session break
- Reviewer verdict: at minimum PARTIAL (if documentation review only) or PASS (if run includes independent verification)

**What still could NOT be claimed even after success:**
- That multi-session continuity works for any project type beyond the scope of the campaign project
- That the framework handles multi-session builds with independent non-coder operators — this campaign assumes the original framework operator
- That any new domain beyond the campaign project's domain(s) is now Validated

---

### Campaign 3 — Independent Re-Execution: CRUD Domain

**Campaign goal:** Produce the first independent re-execution proof on file for an existing Validated domain. The CRUD / Local-State domain is the correct starting point: it is the simplest domain, it has the clearest MUST requirements (10), and it establishes the re-execution template for the four remaining Validated domains.

**Minimum artifact set:**
- Validation run log: `validation/runs/crud-local-state-independent-reexecution-[date].md` — must declare artifact class (Class 3), name the independent operator, and record the execution environment
- Evidence packet: `validation/evidence-packets/crud-local-state-independent-reexecution-[date].md` — independently filed; must not be appended to or merged with the original evidence packet
- Screenshots at key verification points for all 10 MUST requirements
- Reviewer verdict: `validation/reviews/crud-local-state-independent-reexecution-review-[date].md`

**Required verification mode:** Independent operator — a party other than the original build operator — re-executes the task tracker application against all 10 original MUST requirements. Execution must be live (the software is actually run), not a documentation review. The operator must file their own artifact trail independently.

**What counts as success:**
- 10/10 MUST requirements verified at Proven by the independent operator
- All artifacts filed with the operator's name and the execution environment recorded
- Reviewer verdict PASS (or PARTIAL if any gap remains)
- If PASS: the CRUD domain achieves its first PASS reviewer verdict, satisfying the re-execution requirement for that domain

**What still could NOT be claimed even after success:**
- That independent re-execution is complete for the other four Validated domains — each requires its own separate campaign
- That the framework is validated for any domain currently Untested
- That the independent operator represents the framework's target audience (a non-coder founder) unless the operator actually is one — this campaign may or may not close gap 8.5 from `validation/publication-readiness-checklist.md`, depending on who the independent operator is

---

## 7. What Must Not Be Said Publicly Yet

The following are explicit forbidden claims under current evidence. They apply to all public-facing materials: README, launch announcements, marketing copy, social media, book editions, and any derivative content derived from the manuscript.

**1. No claim that the framework handles backend, API, or database work at a validated level.**
Backend / API / Database is Untested. Doctrine exists. No project has been built under governance in this domain.

**2. No claim that authentication or authorization has been governed or tested.**
Authentication / Authorization is Untested. No governed project has implemented auth flows under this framework.

**3. No claim that payment processing or PCI compliance governance is field-tested.**
Payments / Compliance is Untested. The PCI overlay is doctrine. No payment project has been built.

**4. No claim that production deployment has been governed or exercised.**
Production Deployment / Runtime is Untested. All validated pilots were client-side applications with no production server.

**5. No claim that multi-session continuity is field-tested.**
Multi-Session Continuity is Partially Validated. The handoff protocol is designed. No complete multi-session project run is on file.

**6. No claim that real-time or event-driven systems can be built under this framework.**
Real-Time / Event-Driven is Untested with no doctrine. WebSocket/SSE patterns are undocumented.

**7. No claim that AI or LLM workflows can be governed under this framework.**
AI / LLM Workflow Integration is Untested with no doctrine.

**8. No claim that the framework has been validated by an independent non-coder founder.**
Both pilots were conducted by the framework designer. The core audience claim — that non-coder founders can govern AI-built software — has not been independently verified with an external operator.

**9. No expansion of validated scope qualifiers by implication.**
"Email format validation proven" does not imply broader form validation. "In-memory search proven" does not imply server-side search. "Desktop and mobile layout confirmed" does not imply named physical devices unless physical device re-execution is on file. Labels cannot be widened by analogy.

**10. No claim that any Untested domain has been addressed by the addition of governance documentation.**
Writing a domain overlay, protocol, or governance document does not move that domain from Untested to Validated. Protocol ≠ proof. This applies to the UI Validation Protocol, the LLM Operating Discipline, and any future governance document.

---

## 8. Change-Control Rule

Any expansion of a public claim beyond the boundaries current as of 2026-03-18 must follow this sequence in full. There are no shortcuts.

1. **Complete the validation work.** Execute a real governed project or run in the target domain. Do not plan the claim expansion before the work is done.

2. **Produce the evidence artifacts.** File the run log in `validation/runs/`, the evidence packet in `validation/evidence-packets/`, and the reviewer verdict in `validation/reviews/`. Use the templates in `validation/templates/`. Incomplete artifact trails do not satisfy this step.

3. **Update the domain matrix.** Change the domain status in `validation/domain-matrix.md` in the same commit as the reviewer verdict. No status change without a co-filed reviewer verdict.

4. **Update the validation ledger.** Reflect the new status and artifact links in `validation/validation-ledger.md` in the same commit.

5. **Update the Appendix B source.** Revise `validation/appendix-b-source.md` to reflect the new domain status and scope boundary.

6. **Regenerate the candidate manuscript.** Re-execute the insertion patch against the updated `appendix-b-source.md` and produce a new candidate. Re-run `validation/manuscript-candidate-final-review.md` against the new candidate.

7. **Update public-facing materials last.** README, announcements, and marketing copy reflect the SSOT — they do not lead it. Public framing changes only after the repo SSOT is updated and verified.

Skipping any step in this sequence produces a state where public claims outrun the evidence. That is the failure mode this framework exists to prevent.

---

## 9. Closeout Note

The repo-side publication control program is complete as of 2026-03-18.

All required artifacts are filed. The SSOT CI workflow is green. The candidate manuscript is verified against the repo SSOT. The human editorial spot-check checklist is ready for use. No further repo work is required to support publication of the candidate manuscript within its current evidence boundaries.

This file governs what comes after publication — how the framework's evidence base grows, in what order, and under what rules. It does not affect the publication decision. It does not change any current claim. It is a standing governance document for the validation program's next phase.

The next work is validation work, not documentation work.

---

_Created: 2026-03-18. One new repo file only. No manuscript edits. No domain status changes. No edits to domain-matrix.md, validation-ledger.md, README.md, or any existing file._
