# Publication Readiness Checklist

**Canonical publication gate for the book/framework pair.**

This file is the final go/no-go control document before any of the following occur:

- Public release of *The CTO Build Book*
- Broad marketing claims about framework capability
- Major README reframing or expanded positioning
- Manuscript finalization and submission to publisher or printer
- Any public announcement that implies commercial-scale or multi-domain validation

It translates the evidence state in `validation/evidence-coverage-matrix.md` and the editorial findings in `validation/manuscript-framework-crosswalk.md` into a concrete, checkable gate.

**Cross-reference files:**
- `validation/evidence-coverage-matrix.md` — practice-level evidence status (source of truth for what is proven vs. doctrine)
- `validation/manuscript-framework-crosswalk.md` — claim-by-claim safety analysis
- `validation/domain-matrix.md` — canonical domain validation status
- `validation/validation-ledger.md` — evidence chain tracking

**Date created:** 2026-03-17
**Who uses this:** Framework owner, before any of the publication trigger events listed above.
**How to use:** Work through each checklist section. No item in a "Required Before Publish" row may remain incomplete at publication time. Items marked "Recommended Before Broader Claims" do not block narrow-scope publication but block any repositioning or expanded marketing.

---

## Current Publication Posture

**Conditionally ready for narrow-scope publication under current evidence boundaries.**

What this means in plain English:

The book and framework can be published now if and only if the manuscript accurately represents the evidence — which means: narrow claims for proven domains, explicit "designed for, not yet field-tested" language for doctrine domains, and no claims at all for untested areas. The framework's honest position is strong within its proven scope. The risk is not that the framework is weak — it is that marketing, revision, or editorial polish could inadvertently expand the claims beyond what the evidence supports.

**Broader positioning is blocked.** Any framing that presents the framework as multi-domain validated, commercially tested, or proven for backend/auth/payment/deployment use cases would be unsupported by current evidence. This block lifts only when corresponding validation work is completed and artifacts are filed.

**What is publishable now:**
- The governance loop and operating model for Standard-class client-side applications
- The proof-boundary doctrine and evidence discipline
- The five validated domains within their stated scope boundaries
- The honest position on unproven domains

**What is not publishable now:**
- Any claim that the framework handles backend, auth, payments, deployment, or real-time at a validated level
- Any claim that multi-session builds or complex/domain-heavy/specialist project classes are field-tested
- Any claim that rollback-under-failure has been demonstrated in practice
- Any framing that implies commercial-release governance has been exercised
- Any use of "proven" or "validated" for domains listed as Doctrine Only or Untested in `domain-matrix.md`

---

## Checklist

### Section 1 — SSOT Integrity

These items ensure the repo is internally consistent before any external release.

| # | Item | Status | Notes |
|---|------|--------|-------|
| 1.1 | `validation/domain-matrix.md` reflects current evidence — no domain is marked Validated without an evidence packet and reviewer verdict on file | **Complete** | Five domains Validated; all have PARTIAL reviewer verdicts; acknowledged in domain-matrix.md |
| 1.2 | `validation/validation-ledger.md` matches `domain-matrix.md` — no status divergence between the two files | **Complete** | Both files show the same five Validated domains with PARTIAL verdicts as of 2026-03-17 |
| 1.3 | `validation/evidence-coverage-matrix.md` is current and reflects the same status as the ledger and matrix | **Complete** | Created 2026-03-17; reflects current state |
| 1.4 | `validation/manuscript-framework-crosswalk.md` is current against the manuscript draft | **Complete** | Created 2026-03-17 against the full manuscript; must be re-verified if manuscript is revised |
| 1.5 | No domain status has been silently upgraded — every Validated row has a corresponding artifact trail | **Complete** | All five Validated domains have evidence packets and reviewer verdicts on file; all verdicts PARTIAL |
| 1.6 | The PARTIAL reviewer verdict note is present in README.md for all five Validated domains | **Complete** | README contains scope note referencing PARTIAL verdicts and re-execution requirement |
| 1.7 | `CLAUDE.md` proof-boundary doctrine is enforced — no agent or session has silently upgraded claims | **Complete** | CLAUDE.md is current; doctrine consistently enforced throughout all recent work |

---

### Section 2 — Claim-Boundary Control

These items ensure that the claims in all public-facing documents do not outrun the evidence.

| # | Item | Status | Notes |
|---|------|--------|-------|
| 2.1 | Every domain listed as Validated in public materials carries the exact scope boundary from `domain-matrix.md` — not a paraphrase | **Required Before Publish** | README domain table has good coverage but some rows lack the one-line scope qualifier (e.g., "Form Validation" row does not say "email format only") |
| 2.2 | "Form Validation" is scoped to "client-side email format validation" wherever it appears publicly | **Required Before Publish** | Domain matrix notes this; README domain table and manuscript Ch.12 must both carry this qualifier explicitly |
| 2.3 | "Search / Filtering" is scoped to "real-time name/company search and category filtering within Pilot 2 scope" | **Required Before Publish** | Scope is noted in evidence-coverage-matrix; must appear in Ch.12 and Appendix B |
| 2.4 | "Responsive UI" is scoped to "founder-verified on desktop and mobile; device details not recorded; physical device re-execution outstanding" | **Required Before Publish** | automated run (responsive-002) adds Playwright layout checks but does not close device-detail gap |
| 2.5 | Commercial Release Gate is framed as "designed and documented; not yet exercised in a commercial build" everywhere it appears | **Required Before Publish** | Crosswalk identified this as high-risk Zone 3; verify Ch.8-9 language in final draft |
| 2.6 | Rollback under failure is framed as "protocol designed and documented; pilots had no escalation events requiring it" | **Required Before Publish** | Neither pilot triggered rollback; crosswalk identified as Zone 2; verify Ch.8 language |
| 2.7 | Deployment governance, CI/merge governance, auth, and backend are framed as "doctrine only; not yet field-tested" | **Required Before Publish** | All four appear in domain matrix as Untested; framing in Ch.9 and Ch.12 must match |
| 2.8 | Real-Time, VoIP, and AI/LLM Workflow domains are either removed from public claims or carry explicit "out of scope / no doctrine" disclaimers | **Required Before Publish** | Three domains are Untested with no doctrine; any claim about them is unsupported |
| 2.9 | Parallel agent / swarm execution is framed as "doctrine only; not exercised" | **Required Before Publish** | Doctrine exists; no field evidence; verify Ch.11 framing |
| 2.10 | The multi-session continuity caveat is present and unaltered in Ch.11 | **Required Before Publish** | Must confirm caveat survived any revision pass: "hasn't been field-tested the way single-session governance has" |
| 2.11 | Domain-Heavy and Specialist project class caveats are present and unaltered in Ch.11/Ch.13 | **Required Before Publish** | Must confirm: "designed into the system, but they haven't been field-tested" appears verbatim |
| 2.12 | No public document uses "validated" for a domain listed as Untested or Doctrine Only in `domain-matrix.md` | **Required Before Publish** | Systematic check against manuscript Ch.12 and Appendix B required |

---

### Section 3 — Manuscript Safety

These items address the specific risks identified in `validation/manuscript-framework-crosswalk.md`.

| # | Item | Status | Notes |
|---|------|--------|-------|
| 3.1 | Ch.6 "What You Can Honestly Claim" section is present and unedited — it accurately states the narrow validated range | **Required Before Publish** | Confirm this section survived final revision passes; it is the most important guardrail in the book |
| 3.2 | Ch.13 "Designed For Is Not Proven In" section is present and unedited | **Required Before Publish** | Confirm this section exists and is intact in the final draft |
| 3.3 | Appendix B exists and was generated from the live `domain-matrix.md` and `evidence-coverage-matrix.md` — not from memory | **Required Before Publish** | Ch.14 explicitly references Appendix B; if it doesn't exist or is inaccurate, the book contradicts its own SSOT |
| 3.4 | Appendix B domain statuses match `validation/domain-matrix.md` exactly — same labels, same scope qualifiers | **Required Before Publish** | Any mismatch is an overclaim; must verify before submission |
| 3.5 | No chapter presents the founder-as-orchestrator model as independently validated with external non-coder operators | **Required Before Publish** | Both pilots were built by the framework designer; independent external operator verification is outstanding |
| 3.6 | Ch.7 Playwright/verification references are scoped to "used in pilots; formal artifact trail filed for responsive-002 specifically" | **Recommended Before Broader Claims** | Playwright was used informally in pilots; responsive-002 is the only formally filed run |
| 3.7 | Ch.5 LLM operating discipline is framed as "practiced in the pilots" not "proven to prevent all classes of LLM error" | **Required Before Publish** | Evidence is partial; individual techniques lack standalone proof |
| 3.8 | Risk scoring and deploy gate references in Ch.10 are framed as "scoring model designed; not automated or field-exercised" | **Recommended Before Broader Claims** | Risk scoring is doctrine; no automated system has been exercised |

---

### Section 4 — Evidence Chain Completeness

These items track whether the evidence chain for each Validated domain is complete enough to support its published status.

| # | Item | Domain | Status | Required For |
|---|------|--------|--------|-------------|
| 4.1 | Evidence packet filed with no gaps | CRUD / Local-State | **Partial** — screenshots not in repo | Narrow-scope publish: acceptable with acknowledged gap. Full validation: must file screenshots or note as permanently missing. |
| 4.2 | Evidence packet filed with no gaps | Client-Side Multi-Page | **Partial** — screenshots not in repo | Same as 4.1 |
| 4.3 | Evidence packet filed with no gaps | Search / Filtering | **Partial** — screenshots not in repo | Same as 4.1 |
| 4.4 | Evidence packet filed with no gaps | Form Validation | **Partial** — screenshot not in repo | Same as 4.1 |
| 4.5 | Evidence packet filed with no gaps | Responsive UI | **Partial** — screenshots not in repo, device details not recorded | Most material gap; device detail absence is the primary weakness for this domain |
| 4.6 | Independent human re-execution on file with full artifact trail | All 5 Validated domains | **Not started** — all five domains outstanding | Required Before Broader Claims — blocks full Validated status per current doctrine; does not block narrow-scope publication |
| 4.7 | Physical device verification for Responsive UI filed | Responsive UI | **Not started** | Required Before Claiming "verified on real devices" |
| 4.8 | Multi-session continuity: at least one complete multi-session project run on file | Multi-Session | **Not started** | Required Before Any "field-tested" claim for this domain |
| 4.9 | Rollback under failure: at least one governed build exercise where rollback was triggered and documented | Rollback protocol | **Not started** | Required Before Any "tested under failure" claim |
| 4.10 | Backend/API pilot: at least one project under full governance with filed evidence | Backend | **Not started** | Required Before Expanding Validated Range to this domain |

---

### Section 5 — Validation Artifact Hygiene

These items ensure the artifact infrastructure is usable and internally consistent.

| # | Item | Status | Notes |
|---|------|--------|-------|
| 5.1 | All reviewer verdicts for Validated domains are filed | **Complete** — all PARTIAL | Five reviewer verdict files exist; all PARTIAL; gaps acknowledged |
| 5.2 | Reviewer verdicts accurately state what was reviewed and what is outstanding | **Complete** | All verdicts note documentation review scope and outstanding independent re-execution |
| 5.3 | `validation/validation-run-index.md` has no broken links or missing references | **Complete** | Run index is current as of 2026-03-17; five runs registered; responsive-002 corrected in Slice 1 |
| 5.4 | Reconstructed-app artifacts are not cited as original pilot evidence | **Complete** | domain-matrix.md, evidence-coverage-matrix.md, and run index all clearly separate Class 2/3 from Class 1 |
| 5.5 | responsive-002 automated run is labeled as Class 2 source / Class 3 result in all filing locations | **Complete** | Run log, evidence packet, and run index all carry correct classification |
| 5.6 | Human re-execution protocol for Responsive UI remains in PLANNED state — not contaminated with automated run data | **Complete** | Fixed in Slice 1; protocol is clean and unexecuted |
| 5.7 | `validation/templates/` are usable for future runs without requiring modification | **Complete** | Templates exist and have been validated through use in responsive-002 |

---

### Section 6 — Repo Consistency

These items ensure the repo presents a consistent and non-contradictory picture across all files.

| # | Item | Status | Notes |
|---|------|--------|-------|
| 6.1 | README.md domain matrix matches `validation/domain-matrix.md` exactly | **Partial** | README table is accurate on domain statuses but lacks scope qualifiers on several rows (e.g., Form Validation, Responsive UI) |
| 6.2 | README.md scope note (PARTIAL reviewer verdicts, re-execution requirement) is present and accurate | **Complete** | Scope note is present in README |
| 6.3 | No file in the repo contradicts the proof-boundary doctrine | **Complete** | All recent files consistently apply the doctrine |
| 6.4 | CLAUDE.md operating constitution is current and correctly governs agent behavior | **Complete** | CLAUDE.md is current as of session start |
| 6.5 | No domain is marked Validated in one file and Untested in another | **Complete** | Ledger and matrix are consistent |
| 6.6 | `evidence-coverage-matrix.md`, `manuscript-framework-crosswalk.md`, and this file are mutually consistent | **Complete** | All three files produced in same session from same evidence base |

---

### Section 7 — Public-Facing Framing

These items address what the world sees first — README, any launch announcement, marketing copy.

| # | Item | Status | Notes |
|---|------|--------|-------|
| 7.1 | README domain table scope qualifiers added — specifically "email format only" for Form Validation and device-detail note for Responsive UI | **Required Before Publish** | README table is the first thing readers see; missing qualifiers overstate the evidence |
| 7.2 | Any external marketing copy or launch announcement has been reviewed against `evidence-coverage-matrix.md` before publication | **Required Before Publish** | No marketing copy reviewed yet; this gate must be applied at launch time |
| 7.3 | The repo introduction does not claim validation for any domain listed as Untested or Doctrine Only | **Complete** | README introduction correctly frames the validated range and uses "designed for" for unproven domains |
| 7.4 | Any testimonials, case studies, or user stories are scoped to the validated project type (Standard-class client-side) | **Required Before Publish** | No testimonials exist yet; if added, they must be scoped |
| 7.5 | No positioning claims "complete," "enterprise-ready," "production-ready for all project types," or similar | **Required Before Publish** | No such claims exist yet; this is a standing check for any future copy |

---

### Section 8 — Outstanding High-Risk Gaps

These are the evidence gaps that pose the highest publication risk. None of these block narrow-scope publication if the manuscript is correctly scoped. All of them block any broader repositioning.

| # | Gap | Risk Level | Impact on Publication |
|---|-----|------------|----------------------|
| 8.1 | **Appendix B not yet verified** — Ch.14 references it but its contents are unknown | **Critical** | If Appendix B misrepresents domain statuses, the book contradicts its own SSOT. Must be verified before submission. |
| 8.2 | **No independent re-execution on physical devices for any Validated domain** — all five have PARTIAL reviewer verdicts | **High** | Blocks full Validated status per current doctrine. Does not block narrow-scope publication but must be disclosed. |
| 8.3 | **Form Validation label breadth** — domain label implies comprehensive form validation; evidence is one email format rule | **High** | A reader could reasonably expect form validation to cover required fields, length limits, and other types. Scope qualifier is mandatory. |
| 8.4 | **Rollback-under-failure never triggered** — protocol designed; neither pilot exercised it | **High** | Any claim about how the system "handles" failures is unverifiable from the pilot record. |
| 8.5 | **Independent non-coder operator never used the framework** — both pilots were the framework designer | **Medium** | The core audience promise ("non-technical founders can do this") has not been independently verified. Acceptable for initial publication with honest framing; blocks strong marketing claims about accessibility. |
| 8.6 | **Multi-session builds not field-tested** — both pilots were single-session | **Medium** | Multi-session continuity claim is doctrine. Manuscript caveats this correctly; must ensure caveat survives final editing. |
| 8.7 | **Screenshot evidence not filed** — original pilot screenshots not in repo for any Validated domain | **Medium** | Evidence packets are marked incomplete; does not invalidate pilot results but is a visible gap in any audit. |
| 8.8 | **Commercial Release Gate never exercised** — designed and documented only | **Medium** | Any implication that the commercial gate "works" is unsupported. Must be framed as "designed for." |

---

### Section 9 — Post-Publication Restrictions

These are standing rules that apply after publication and must be maintained until corresponding evidence is filed.

| # | Restriction | Applies Until |
|---|-------------|---------------|
| 9.1 | Do not add new domains to the Validated list in any public document without filing: evidence packet, run log, reviewer verdict, and independent re-execution proof | Permanent — this is the validation methodology |
| 9.2 | Do not upgrade "Partially Validated" or "Doctrine Only" domains to "Validated" in any marketing copy, README update, or book revision without corresponding artifacts | Permanent |
| 9.3 | Do not present the framework as validated for Commercial Release builds — Personal Production Gate only — until Commercial Release Gate is exercised with evidence on file | Until Commercial Release Gate run is filed |
| 9.4 | Do not claim multi-session continuity is field-tested until at least one multi-session project run is on file | Until multi-session run is filed |
| 9.5 | Do not claim rollback-under-failure has been tested until at least one governed rollback event is documented | Until rollback exercise artifact is filed |
| 9.6 | Do not present the framework as validated for independent non-coder operators until an external operator completes a governed build with an artifact trail | Until external operator run is filed |
| 9.7 | Any new edition of the book must trigger a re-verification of Appendix B against the live `domain-matrix.md` before that edition is submitted | At each new edition |
| 9.8 | Manuscript revisions that touch domain claims, project class descriptions, or governance capability claims must be re-reviewed against `manuscript-framework-crosswalk.md` | At each revision pass |

---

## Current Publication Decision

**Narrow-scope publication: CONDITIONALLY READY.**

The book and framework may be published under current evidence boundaries if, and only if, the following conditions are satisfied before submission:

1. **Appendix B exists and accurately reflects `domain-matrix.md`** — this is the single highest-priority required action. (Item 3.3, 3.4)
2. **Ch.6 "What You Can Honestly Claim" is present and unedited** in the final draft. (Item 3.1)
3. **Ch.13 "Designed For Is Not Proven In" is present and unedited** in the final draft. (Item 3.2)
4. **Every domain claim in Ch.12 carries its scope qualifier** — no bare domain label without explicit scope limit. (Item 2.1–2.12, 3.4)
5. **Commercial Release Gate is framed as doctrine, not proven** in Ch.8-9. (Item 2.5)
6. **Multi-session and non-Standard class caveats are preserved** in Ch.11. (Item 2.10, 2.11)
7. **README domain table scope qualifiers are added** for Form Validation and Responsive UI at minimum. (Item 7.1)

**Broader positioning: BLOCKED.**

Any of the following would make publication unsafe under current evidence:

- Presenting any doctrine-only domain (backend, auth, payments, deployment, real-time) as field-tested or validated
- Removing or softening the caveats in Ch.6, Ch.11, Ch.13, or Ch.14
- Publishing Appendix B that does not match the live repo's domain status
- Marketing copy that implies multi-domain validated capability
- Any "proven to work for X" claim where X is not CRUD, client-side multi-page, search/filtering (narrow), form validation (email only), or responsive layout

**The honest narrow-scope position is strong.** Two pilots, 24 requirements proven, zero scope drift, both gates passing — for Standard-class client-side applications. That is a real, defensible, evidence-backed claim. Publish that position with confidence and without inflation.

---

## Top Blockers

In order of priority:

1. **Appendix B** — must exist and must match live repo before submission. No other action matters as much as this one.
2. **Scope qualifiers on domain claims** — Ch.12 and README.md both need one-line scope qualifiers on every Validated domain. "Form Validation" must say "email format only." "Responsive UI" must say "device details not recorded."
3. **Commercial Release Gate and rollback framing check** — scan Ch.8-9 for any "proven" or "tested" language near these two items; revise to "designed for."
4. **Caveat preservation check** — read the final draft of Ch.11, Ch.13, Ch.14 and confirm the honest caveats survived the last revision pass.
5. **Marketing copy gate** — before any launch announcement or marketing copy is published, review it against `evidence-coverage-matrix.md` and this checklist.

---

## Next Actions After This Checklist

These are the strongest next steps, ordered by impact on either publication safety or evidence expansion.

| Priority | Action | Type | Impact |
|----------|--------|------|--------|
| 1 | **Locate or draft Appendix B and verify it against `domain-matrix.md`** | Editorial | Eliminates the single highest-risk gap before publication |
| 2 | **Read final manuscript draft of Ch.6, Ch.8-9, Ch.11, Ch.12, Ch.13, Ch.14 against crosswalk and checklist** | Editorial | Confirms or flags each Required Before Publish item in the manuscript |
| 3 | **Add scope qualifiers to README domain table** | Repo — trivial edit | Closes Item 7.1; aligns public repo with evidence |
| 4 | **Execute independent human re-execution for CRUD domain** | Validation work | Closes 4.6 for one domain; begins satisfying re-execution requirement; opens path to first full PASS reviewer verdict |
| 5 | **Execute responsive UI human re-execution on physical devices** | Validation work | Closes 4.7; closes device-detail gap; strongest remaining domain evidence gap |
| 6 | **Conduct a multi-session governed build** | Validation work | Closes 4.8; converts multi-session from Partially Supported to Proven; allows removing caveat from book in future editions |
| 7 | **Conduct a governed build with an independent non-coder operator** | Validation work | Closes 8.5; validates the core audience promise; strongest single piece of evidence that could be added |
| 8 | **Execute a Phase 2 backend pilot** | Validation work | Expands the validated range to its next natural boundary; enables broader positioning |

---

## Maintenance

This file must be updated:

1. When any Required Before Publish item is completed — change status to Complete and note the date
2. When any new validation work is completed and a domain status changes
3. When the manuscript is revised in a way that touches claim scope
4. When Appendix B is drafted or revised

Do not update statuses without a corresponding artifact. Status changes in this file must trace to a filed artifact in `validation/`.

---

_Created: 2026-03-17. One new file only. No domain status changes. No edits to manuscript, README, domain-matrix, or validation-ledger._
