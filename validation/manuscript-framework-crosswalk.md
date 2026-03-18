# Manuscript-to-Framework Crosswalk

**Purpose:** Editorial safety bridge between the manuscript (*The CTO Build Book: How Non-Technical Founders Ship Real Software Using AI*) and the `cto-build-framework` repo. This file maps major manuscript claims to their current repo support level, identifies safe framing boundaries, and surfaces editorial actions needed before publication.

**Scope:** One file. Read-only relationship to manuscript. No domain status changes. No edits to domain-matrix, validation-ledger, or README.

**Cross-reference files:**
- `validation/evidence-coverage-matrix.md` — practice-level evidence status
- `validation/domain-matrix.md` — domain validation status
- `validation/validation-ledger.md` — canonical high-level domain ledger

**Date created:** 2026-03-17
**Maintained by:** Framework owner — update when manuscript chapters are revised or new validation work changes evidence state.

---

## Support Legend

| Symbol | Label | Meaning |
|--------|-------|---------|
| **DE** | Direct Evidence Support | Claim is backed by a filed evidence packet, run log, and reviewer verdict in this repo. Safe to claim as demonstrated. |
| **DS** | Doctrine Design Support Only | Claim describes a designed governance mechanism. No field execution evidence. Safe to claim as "designed for" or "built into the system" — not safe to claim as proven. |
| **PS** | Partial Support — Narrow Wording Required | Some evidence exists but it is incomplete, scope-limited, or PARTIAL verdict only. Claim is safe with explicit scope qualifiers. Without qualifiers, the claim overstates the evidence. |
| **UN** | Unsupported — Do Not Claim Broadly | No evidence. No published doctrine in repo. Claim would be fabricated. Scope must be disclaimed entirely or removed. |

---

## Crosswalk Table

| Manuscript Section / Claim Area | Support Level | Repo Support Source(s) | Safe Framing Boundary | Editorial Action Needed |
|----------------------------------|---------------|------------------------|----------------------|-------------------------|
| **Ch.1 — The system, not the genius** (CTO role as orchestrator, not coder) | **DE** | `governance/`, pilot evidence, six-phase loop artifacts | Safe as stated. Founder-as-orchestrator is demonstrated across both pilots. | None |
| **Ch.1 — Task Tracker pilot story** (first build, iterative delivery) | **DE** | `validation/evidence-packets/task-tracker-client-side-crud.md`, pilot logs | Safe as stated. Evidence packet filed (incomplete screenshots, but execution is on record). | Note screenshot gap if precision is required in Appendix B |
| **Ch.2 — Six-phase governance loop** (Scope → Architecture → Build → Verify → Gate → Release) | **DE** | `governance/six-phase-loop.md`, both pilot runs | Safe as stated. Both pilots exercised the full loop. | None |
| **Ch.2 — Slice-based delivery** (micro-slices with checkpoints) | **DE** | Both pilot runs, `governance/llm-operating-discipline.md`, `validation/evidence-coverage-matrix.md` | Safe as stated. Consistently demonstrated across all framework work. | None |
| **Ch.2 — Checkpoint system** (gate before next slice) | **PS** | Both pilots demonstrate informal checkpoints; no formal gate log filed separately | Safe with qualifier: "checkpoints exercised in pilot builds." Not safe to claim as a formally logged gate system with artifact trails. | Add qualifier or acknowledge gates were informal in pilots |
| **Ch.3 — Scope definition and PRD process** | **PS** | Scope artifacts exist for both pilots; template system documented | Safe to claim as documented practice. Scope drift prevention is demonstrated. Full PRD governance for complex projects is doctrine. | Qualify: "demonstrated for Standard-class projects" |
| **Ch.4 — Architecture patterns for client-side apps** | **DE** | Both pilot builds, contact manager + task tracker | Safe as stated for client-side, single-file, localStorage apps. | Keep scope qualifier: "client-side architecture" |
| **Ch.4 — Architecture for backend / API / database projects** | **DS** | `governance/` domain overlays, architecture doctrine | Not safe to claim as demonstrated. Designed for, not field-tested. | Add explicit qualifier: "designed into the system; not yet field-tested at the time of writing" |
| **Ch.5 — Build phase, LLM operating discipline** (structured prompting, environment hygiene) | **PS** | `governance/llm-operating-discipline.md`, pilot runs (partially documented) | Safe to claim as practiced discipline. Evidence for individual techniques is partial — not all practices have standalone proof. | "Practiced in the pilots" is safe; "proven to prevent all classes of LLM error" is not |
| **Ch.5 — Scout/mapper passes before execution** | **PS** | Referenced in pilot logs; no standalone test artifact | Safe as described practice. Not safe to claim as formally validated technique. | Keep as best-practice framing, not validated-method framing |
| **Ch.5 — Session decay management and handoff documents** | **PS** | Handoff docs exist in repo; multi-session continuity domain is Partially Validated | Safe to claim as designed practice. Full multi-session field test not on file. | Qualifier recommended: "protocol designed and documented; comprehensive field test outstanding" |
| **Ch.6 — Five truth-state progression** (Planned → Implemented → Tested → Proven → Honestly Claimable) | **DE** | `governance/`, `validation/evidence-coverage-matrix.md`, manifest throughout validation program | Safe as stated. The framework itself demonstrates this progression. | None |
| **Ch.6 — Proof-boundary doctrine** ("only claim what evidence supports") | **DE** | Manifest throughout repo SSOT design, `CLAUDE.md`, evidence-coverage-matrix | Safe as stated. The doctrine is a first-class design principle with consistent application. | None |
| **Ch.6 — "What You Can Honestly Claim" section** | **DE** | Manuscript already self-applies proof-boundary doctrine here; aligns with repo status | Safe as written. Manuscript accurately states the validated range as narrow. | Verify Appendix B accurately reflects current `domain-matrix.md` and `evidence-coverage-matrix.md` |
| **Ch.6 — Evidence Discipline section** | **DE** | `validation/` infrastructure, `CLAUDE.md` rules | Safe as stated. | None |
| **Ch.7 — Verification phase, Playwright testing** | **PS** | responsive-002 Playwright run (Class 2 source / Class 3 result); CRUD and multipage pilots used Playwright implicitly | Safe to claim as practiced. responsive-002 is the only formally filed Playwright run with full artifact trail. | Qualify: "Playwright used across pilots; formal artifact trail filed for responsive-002 specifically" |
| **Ch.7 — Visual verification** | **PS** | Screenshots exist for responsive-002; original pilot screenshots not in repo | Safe to claim as practiced. Screenshot evidence gaps acknowledged in ledger. | None if acknowledged; add disclaimer if presenting screenshots as comprehensive |
| **Ch.8 — Personal Production Gate** (founder review before release) | **DE** | Both pilots completed gate review; gate is documented in `governance/` | Safe as stated for Standard-class client-side projects. | Keep scope qualifier: "personal production builds, not commercial-release deployments" |
| **Ch.8 — Commercial Release Gate** (security, compliance, legal review) | **DS** | `governance/` — PCI overlay, auth overlay; gate design documented | Not safe to claim as demonstrated. Designed for, not exercised. | Must qualify: "designed into the governance system; not yet exercised in a production commercial build" |
| **Ch.8 — Rollback under failure** | **DS** | Rollback protocol documented; neither pilot triggered an escalation or rollback event | Not safe to claim as field-tested. Zero escalation events in pilot record. | Qualify: "rollback path is designed and documented; pilots had no escalation events requiring it" |
| **Ch.9 — Deployment governance** | **DS** | Domain overlay documented; no deployment exercised under governance | Not safe to claim as demonstrated. Doctrine only. | Add explicit qualifier: "deployment domain is designed but not yet field-tested" |
| **Ch.9 — CI / branch / merge governance** | **DS** | Branch governance documented; no project exercised CI pipeline under governance | Doctrine only. | Qualifier required |
| **Ch.10 — Audit separation** (builder ≠ verifier, four-layer model) | **DE** | `governance/`, validation program design, reviewer verdict infrastructure | Safe as stated as structural design. Separation enforced in validation review trail. | None |
| **Ch.10 — Risk scoring and deploy gates** | **DS** | Risk scoring documented; no automated scoring system exercised | Doctrine. | Qualify: "risk scoring model designed; not yet automated in a live deployment pipeline" |
| **Ch.11 — Multi-session continuity** | **PS** | Protocol designed; handoff docs exist; no complete multi-session project run on file | Manuscript already caveats this honestly: "hasn't been field-tested the way single-session governance has." | Keep that caveat verbatim — it is accurate. Do not strengthen claim. |
| **Ch.11 — Four Project Classes** (Standard, Complex, Domain-Heavy, Specialist) | **PS** | Standard class demonstrated; Complex/Domain-Heavy/Specialist are doctrine | Manuscript already states Domain-Heavy and Specialist "haven't been field-tested." | Keep that statement. Verify it appears in final draft. Do not quietly remove the caveat. |
| **Ch.11 — Swarm / parallel agent execution** | **DS** | Multi-agent orchestration doctrine documented; not exercised | Doctrine only. | Qualify: "parallel agent execution is designed into the system; not yet field-tested" |
| **Ch.12 — Honest Position on Domains** | **DE** | `validation/domain-matrix.md`, `validation/validation-ledger.md` | Manuscript's honest framing of domain limitations aligns with repo. | Verify the domain list and status labels in this chapter match current `domain-matrix.md` exactly |
| **Ch.12 — CRUD / Local-State claim** | **DE** | `validation/evidence-packets/task-tracker-client-side-crud.md`, reviewer verdict filed | Safe. Validated domain. | Note: reviewer verdict is PARTIAL; independent re-execution is outstanding. Acceptable for "Validated" framing if acknowledged in Appendix B. |
| **Ch.12 — Client-Side Multi-Page claim** | **DE** | `validation/evidence-packets/contact-manager-client-side-multipage.md` | Safe. Validated domain. | Same PARTIAL caveat applies. |
| **Ch.12 — Search / Filtering claim** | **PS** | `validation/evidence-packets/contact-manager-search-filtering.md` — R-05 and R-06 only | Safe with narrow wording. "Real-time search and category filtering demonstrated within Pilot 2 scope" is accurate. Broad "search proven" is not. | Use narrow framing in chapter and Appendix B |
| **Ch.12 — Form Validation claim** | **PS** | `validation/evidence-packets/contact-manager-form-validation.md` — R-09 only (client-side email format) | Very narrow evidence. "Email format validation demonstrated" is safe. "Form validation proven" is not — no other field types tested. | Must use narrow wording: "client-side email format validation" not "form validation" generically |
| **Ch.12 — Responsive UI claim** | **PS** | `validation/evidence-packets/responsive-ui-both-pilots.md` (PARTIAL) + responsive-002 automated Playwright run (Class 2 source, PARTIAL) | Automated run: 10/10 layout checks PASS on reconstructed apps. Physical device verification outstanding. | Qualify: "layout verified by Playwright on reconstructed apps; physical device re-execution outstanding" — do not claim "verified on real devices" |
| **Ch.12 — Authentication / Authorization claim** | **DS** | Doctrine overlay documented; no project built | Doctrine only. | Must not claim as demonstrated. "System is designed to handle auth" only. |
| **Ch.12 — Backend / API / Database claim** | **DS** | Architecture doctrine documented; no project built | Doctrine only. | Same qualifier as auth. |
| **Ch.12 — Payments / Compliance claim** | **DS** | PCI overlay designed; no project built | Doctrine only. | Must not claim as demonstrated. |
| **Ch.12 — Real-Time / Event-Driven claim** | **UN** | No doctrine. No project. | Do not claim. | Remove or add explicit "not designed or tested" disclaimer. |
| **Ch.12 — VoIP / Telephony claim** | **UN** | No doctrine. No project. | Do not claim. | Remove or add explicit "out of scope" disclaimer. |
| **Ch.12 — AI / LLM Workflow Automation claim** | **UN** | No doctrine. No project in this repo. | Do not claim. | Remove or add explicit disclaimer. |
| **Ch.12 — Production Deployment / Runtime claim** | **DS** | Deployment doctrine documented; no deployment under governance | Doctrine only. | Qualify clearly. |
| **Ch.13 — "Designed For Is Not Proven In"** | **DE** | Proof-boundary doctrine is foundational to repo design | Manuscript correctly names this distinction. | Preserve this section as-is — it is the most important editorial guardrail in the book. |
| **Ch.13 — Domain-Heavy and Specialist class caveats** | **DE** | `validation/domain-matrix.md`, evidence-coverage-matrix — both classes are Doctrine Only | Manuscript already states: "designed into the system, but they haven't been field-tested." | Preserve verbatim. Do not soften or remove. |
| **Ch.14 — "Position You Can Stand Behind"** | **PS** | Manuscript's stated position aligns with repo's current evidence state | Position is honest if Appendix B accurately reflects current evidence. Appendix B must be verified. | Appendix B alignment is the primary action — see below |
| **Ch.14 — Appendix B reference** ("Appendix B shows the current validation status for every major software domain") | **PS** | `validation/domain-matrix.md` and `evidence-coverage-matrix.md` are the sources | Appendix B must be a faithful snapshot of domain-matrix.md and evidence-coverage-matrix.md at time of publication. Any mismatch is an overclaim. | **Critical action:** verify Appendix B content against repo before submission. Update Appendix B if domain statuses change before publication. |

---

## High-Risk Overclaim Zones

These are the manuscript sections most likely to inadvertently misrepresent the evidence state. Each requires explicit verification before publication.

### Zone 1 — Domain Labels Without Scope Qualifiers

**Chapters:** 12 (domain claims), Appendix B

**Risk:** Domain labels like "Form Validation," "Responsive UI," and "Search / Filtering" sound comprehensive. The actual evidence is extremely narrow. A reader could reasonably infer the framework handles all form validation, all responsive UI scenarios, all search implementations — none of which is supported.

**Required action:** Every domain listed as "Validated" in Ch.12 and Appendix B must carry a one-line scope qualifier. Use the scope qualifiers from `validation/domain-matrix.md` directly. Do not paraphrase.

---

### Zone 2 — Rollback and Escalation Claims

**Chapters:** 8, 9

**Risk:** The governance loop includes a rollback protocol. Neither pilot triggered an escalation or rollback event. A claim that the rollback system "works" would be unverifiable from the current evidence record.

**Required action:** Any rollback reference must be framed as "the path is designed and available" — not as "the system has been tested under failure conditions."

---

### Zone 3 — Commercial Release Gate and Compliance

**Chapters:** 8, 9

**Risk:** The book describes a Commercial Release Gate with security, legal, and compliance review layers. This gate has never been exercised. A startup founder reading this chapter could believe the framework has been tested in a commercial deployment context.

**Required action:** Add a short explicit statement that the Commercial Release Gate is designed and documented but not yet exercised in a live commercial build. This statement may already exist — verify it is present in the final draft.

---

### Zone 4 — Multi-Session and Complex Project Classes

**Chapters:** 11

**Risk:** The Four Project Classes section describes how the framework handles Complex, Domain-Heavy, and Specialist projects. Only the Standard class has been field-tested. The other three are doctrine.

**Required action:** Verify the caveat ("haven't been field-tested") is present for all three non-Standard classes in the final draft. Do not allow it to be edited out in a revision pass.

---

### Zone 5 — Appendix B Drift

**Risk:** Appendix B will be written at some point before publication. If written from memory or from an earlier draft, it may not accurately reflect the live `domain-matrix.md`. After any validation work is completed between now and publication, the repo evidence state will change — Appendix B must be updated to match.

**Required action:** Appendix B must be generated directly from `validation/domain-matrix.md` and `validation/evidence-coverage-matrix.md` — not reconstructed from memory. Establish a workflow: before submission, read both files, then write Appendix B from the live state.

---

## Immediate Editorial Priorities

Ordered by publication-risk impact. These are actions the manuscript owner should take before the book is submitted for publication.

| Priority | Action | Why |
|----------|--------|-----|
| 1 | **Verify Appendix B exists and accurately reflects current `domain-matrix.md` and `evidence-coverage-matrix.md`** | Ch.14 explicitly references Appendix B. If it doesn't match the live repo, the book contradicts its own SSOT. |
| 2 | **Add scope qualifiers to all domain claims in Ch.12** | "Form Validation (Validated)" without qualifier implies full coverage. Evidence is R-09 only (email format). Every domain needs a one-line scope limit. |
| 3 | **Verify the Commercial Release Gate is framed as doctrine, not proven** | This claim appears in Ch.8-9. If the word "proven" or "tested" appears anywhere near it, revise to "designed for." |
| 4 | **Verify the multi-session caveat is preserved in Ch.11** | The caveat ("hasn't been field-tested the way single-session governance has") must be present in the final draft. Confirm it was not removed in any revision. |
| 5 | **Verify Domain-Heavy and Specialist class caveats are preserved in Ch.11/Ch.13** | These caveats accurately reflect evidence state. Confirm they survived any revision passes. |
| 6 | **Review any Responsive UI language for physical device claims** | automated Playwright run (responsive-002) used reconstructed apps in headless Chromium. It is not a physical device test. Do not reference it as physical device verification. |
| 7 | **Flag Real-Time, VoIP, and AI/LLM Workflow sections for removal or explicit "out of scope" statements** | These domains have no doctrine and no evidence in this repo. Any claim about them is unsupported. |
| 8 | **Establish Appendix B update protocol** | Agree on a workflow: before submission, regenerate Appendix B from live `domain-matrix.md`. Document who is responsible and when this happens. |

---

## What the Manuscript Gets Right

For completeness: these manuscript elements are accurately aligned with the evidence record and require no editorial correction.

- **Ch.6 proof-boundary doctrine** — honestly stated; matches repo design exactly
- **Ch.6 "What You Can Honestly Claim"** — accurate description of the validated range
- **Ch.11 multi-session caveat** — verbatim acknowledgment of gap; accurate
- **Ch.11 non-Standard class caveats** — "designed into the system, but haven't been field-tested" is accurate
- **Ch.13 "Designed For Is Not Proven In"** — essential guardrail; accurately reflects the distinction this repo enforces
- **Ch.14 "Position You Can Stand Behind"** — honest framing; safe if Appendix B is accurate
- **Standard-class claim scope** — manuscript does not overclaim; correctly limits the proven range to client-side builds

These sections represent the manuscript applying its own doctrine to itself. They must be preserved in any revision.

---

## Maintenance Note

This file is a point-in-time snapshot of manuscript-to-repo alignment as of 2026-03-17. It must be updated when:

1. New validation work is completed and domain statuses change
2. Manuscript chapters are revised in ways that change claim scope
3. Appendix B is drafted or revised

Do not treat this crosswalk as a permanent reference after significant time has passed. Re-run the crosswalk check before submission.

---

_Created: 2026-03-17. One-file slice. No domain status changes. No edits to domain-matrix, validation-ledger, or README._
