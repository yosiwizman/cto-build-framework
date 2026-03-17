# Domain Validation Result

> **Instructions:** Copy this file to `validation/runs/{domain}-result-{date}.md` immediately after completing a human validation run. Fill every field from your own direct observation. Do not fill fields from AI summaries, prior documentation, or memory — only from what you tested and saw during this run.
>
> This document records what happened. It is not a plan. Do not create this file before the run is complete.

---

## Domain

**Domain name:** (e.g., Responsive UI / CRUD Local-State / Search Filtering)

**Pilot(s) covered:** (e.g., Task Tracker — R-08 / Contact Manager — R-11)

---

## Artifact Provenance

> **This section is required. Fill it before recording any results. The artifact class declared here governs what this result document may be used to support. See `validation/domain-matrix.md` — Artifact Classification.**

| Field | Value |
|-------|-------|
| Artifact Class Used | **Select one:** Class 1 — Original Pilot Artifact / Class 2 — Reconstructed Artifact / Class 3 — New Execution Artifact |
| Source Artifact Path | (exact path to the file that was tested, e.g., `reconstructed-apps/task-tracker-reconstructed.html`) |
| Run Type | **Select one:** Original pilot execution / Reconstructed run / New independent validation run |
| Corresponding run log | (link to the run document this result is drawn from, e.g., `validation/runs/responsive-ui-human-reexecution-planned.md`) |

**Provenance Statement (required):**

> "This result was produced using a **[Class X]** artifact. It must not be interpreted as evidence of original pilot execution unless the artifact class is Class 1. Class 2 results demonstrate behavior of a reconstructed artifact only. Class 3 results constitute new independent evidence and must be accompanied by a full artifact trail before any domain status change."

> **Guardrail reminders:**
> - Class 2 results cannot upgrade domain confidence or close artifact gaps in original evidence packets
> - Results from this document may only update `validation/domain-matrix.md` after a reviewer verdict is filed and the artifact class is Class 1 or Class 3
> - Mixing Class 1 and Class 2 evidence in a single claim invalidates the claim
> - If the source artifact is a reconstructed file, label this result document `reconstructed-[date]` and do not file it alongside original pilot evidence

---

## Execution Metadata

| Field | Value |
|-------|-------|
| Run date | YYYY-MM-DD |
| Reviewer name | |
| Reviewer independence | **Confirmed independent** — reviewer was not the original builder of this application / **Not independent** — original builder performed this run (note limitation) |
| Repo commit hash at run start | (run `git log --oneline -1` and paste the result here) |
| Run protocol used | (link to the planned run doc, if one existed — e.g., `validation/runs/responsive-ui-human-reexecution-planned.md`) |

**Desktop device (if tested):**

| Field | Value |
|-------|-------|
| Device name / model | |
| Operating system | |
| OS version | |
| Browser name | |
| Browser version | |
| Screen resolution / viewport | |

**Mobile device (if tested):**

| Field | Value |
|-------|-------|
| Device name / model | |
| Operating system | |
| OS version | |
| Browser name | |
| Browser version | |
| Screen size / form factor | |

---

## Requirements Tested

List every requirement in scope for this run. Record only what you directly observed.

| Requirement ID | Requirement Description | Result | Notes |
|----------------|------------------------|--------|-------|
| | | PASS / FAIL / NOT TESTED | |
| | | PASS / FAIL / NOT TESTED | |
| | | PASS / FAIL / NOT TESTED | |

_Add rows as needed. Do not omit in-scope requirements. If a requirement was not tested during this run, mark it NOT TESTED and explain why in Notes._

---

## Screenshots Captured

List every screenshot taken during this run. A screenshot is only valid if it was captured during this run — do not list screenshots from prior sessions.

| Screenshot Name | Description | File Path |
|-----------------|-------------|-----------|
| | | `validation/screenshots/...` |
| | | |

_If no screenshots were captured, write: "None captured — reason: [explain]." Missing screenshots must be noted as a gap in the Evidence Integrity Statement below._

---

## Observed Failures

List every issue, unexpected behavior, or FAIL result discovered during this run.

_If no failures were observed, write: "None — all in-scope requirements passed."_

- (describe each failure: what was tested, what was expected, what was observed)

---

## Evidence Integrity Statement

> This section must be completed by the person who performed the run. It cannot be filled by an AI tool.

**The reviewer confirms:**

- [ ] This run was performed manually — the reviewer personally opened the software and tested each requirement listed above
- [ ] All PASS results reflect direct observation by the reviewer — not AI assertions or prior documentation
- [ ] All screenshots listed in the Screenshots section were captured during this run on the devices listed in Execution Metadata
- [ ] The commit hash recorded above is the actual repo state at the time of testing
- [ ] No result has been inflated, inferred, or assumed — only directly observed behavior is recorded here

**Reviewer signature / name:** _______________
**Date:** _______________

_If any of the above cannot be checked — for example, if screenshots were not captured or the commit hash was not recorded — note the gap explicitly here rather than leaving the checkbox blank._

---

## Domain Verdict

**Overall result for this run:**

- [ ] **PASS** — all in-scope requirements observed passing; environment details recorded; screenshots filed
- [ ] **PARTIAL** — some requirements passed; conditions or gaps apply (describe below)
- [ ] **FAIL** — one or more requirements failed or run was inconclusive (describe below)

**Conditions or limits (if PARTIAL or FAIL):**

> **Important:** This verdict reflects what was observed in this run. It does NOT automatically change the domain status in `validation/domain-matrix.md` or `validation/validation-ledger.md`. Those files are updated only after a formal reviewer verdict is filed. See Filing Instructions below.

---

## Filing Instructions

After this document is complete and all screenshots are filed, the following artifacts must be updated. Do not update any of these before this document is finished.

| Step | Action | File |
|------|--------|------|
| 1 | File screenshots to `validation/screenshots/{domain}-{date}/` | New directory |
| 2 | File this completed result document to `validation/runs/` | This file |
| 3 | File a formal reviewer verdict referencing this result document | `validation/reviews/{domain}-review-{date}.md` — use `validation/templates/reviewer-verdict-template.md` |
| 4 | After reviewer verdict is filed: update the backlog row for this domain | `validation/validation-ledger.md` |
| 5 | After reviewer verdict is filed: update domain status if verdict supports it | `validation/domain-matrix.md` |

**Do not update `validation/validation-ledger.md` or `validation/domain-matrix.md` on the basis of this result document alone. A reviewer verdict must be filed first (Step 3). The result document is input to the reviewer verdict — it is not a verdict itself.**

---

_This template is part of the CTO Build Framework validation infrastructure. Do not modify the template itself — copy it for each completed run. A result document filled with placeholder text or AI-generated content is not evidence._
