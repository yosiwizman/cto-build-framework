# Human Editorial Spot-Check Checklist

**Type:** Human-review checklist artifact

**Purpose:** Bounded checklist for the final human editorial review of the approved candidate manuscript. Defines exactly what to read, what to confirm, and what must not be changed. Keeps the review focused and prevents reopening settled SSOT decisions.

**Date:** 2026-03-18
**Repo:** https://github.com/yosiwizman/cto-build-framework

---

## Files Under Review

| Role | Exact path |
|------|-----------|
| Approved candidate manuscript | `C:\Users\yosiw\Downloads\ASSEMBLED_MANUSCRIPT_COMPLETE_APPENDIX_B_CANDIDATE.md` |
| Final publication handoff artifact | `C:\Users\yosiw\cto-build-framework\validation\final-publication-handoff.md` |
| Final QA review artifact | `C:\Users\yosiw\cto-build-framework\validation\manuscript-candidate-final-review.md` |

**Use the candidate manuscript.** Do not use the locked baseline (`ASSEMBLED_MANUSCRIPT_COMPLETE.md`) — it contains a missing Appendix B and a placeholder URL.

---

## What the Human Is Checking

This is a style and flow review, not a content review. The domain statuses, scope qualifiers, and disclosure language have been verified by programmatic diff and QA review. The job here is to confirm the candidate reads naturally and renders correctly — not to re-litigate what's in it.

**Scope: lines 2318–2411 of the candidate manuscript.**

That is: the paragraph that references Appendix B (line 2324), the book's final paragraph and closing sentence (lines 2362–2364), and the entire Appendix B insertion (lines 2366–2411).

---

## Checklist Items

### A — URL Sentence (line 2324)

Read the sentence aloud:

> "Appendix B shows the current validation status for every major software domain — what's been proven, what's partially supported, and what remains untested. The companion framework (available free at https://github.com/yosiwizman/cto-build-framework) includes a complete Domain Validation Matrix with the specific evidence required to validate each domain and example projects designed to test them."

- [ ] **A1** — The URL is the correct GitHub URL for the companion framework
- [ ] **A2** — The sentence reads naturally with the URL in place (not awkward or broken)
- [ ] **A3** — There is no residual `[URL]` placeholder anywhere in the document

---

### B — Transition into Appendix B (lines 2362–2368)

Read these lines:

> "That position is yours. You've earned it.
>
> ---
>
> # Appendix B — Domain Validation Status"

- [ ] **B1** — The book's closing sentence ends cleanly before the separator
- [ ] **B2** — The `---` horizontal rule creates a clear visual break between the book body and the appendix
- [ ] **B3** — The `# Appendix B — Domain Validation Status` heading appears once, in the correct position, with no duplication

---

### C — PARTIAL Verdict Disclosure Paragraph (line 2374)

Read the paragraph beginning "Important disclosure: All five Validated domains have PARTIAL reviewer verdicts..."

- [ ] **C1** — The paragraph is present and readable
- [ ] **C2** — Its position (immediately after the status-definitions paragraph, before the domain table) feels appropriate for a reader who needs to understand what "Validated" means in context

---

### D — Domain Table (lines 2378–2395)

Scan the 16-row table.

- [ ] **D1** — All 16 rows are present
- [ ] **D2** — The table is legible and scannable — three columns (Domain, Status, Scope Boundary) are visually clear
- [ ] **D3** — The scope qualifiers for the three narrow domains are present and have not been shortened:
  - Search / Filtering row includes: *"Pilot 2 contact manager only; in-memory/localStorage; server-side search, faceted search, and pagination not tested"*
  - Form Validation row includes: *"one field, one rule"* and *"no server-side validation tested"*
  - Responsive UI row includes: *"device names, OS, and browser not recorded; physical device re-execution outstanding"*
- [ ] **D4** — The 10 Untested rows say "Untested" — none have been silently upgraded

---

### E — "How the Proof Boundary Expands" Section (lines 2397–2401)

Read the section.

- [ ] **E1** — The section reads naturally as a short explanation of how domains move from Untested to Validated
- [ ] **E2** — The companion framework URL (https://github.com/yosiwizman/cto-build-framework) appears correctly in the paragraph

---

### F — "What This Table Does Not Show" Section (lines 2403–2409)

Read the three bullet points.

- [ ] **F1** — The three bullets read clearly and make plain-English sense to a founder reader
- [ ] **F2** — The closing line of the appendix (line 2411) reads naturally: *"The companion framework is available at https://github.com/yosiwizman/cto-build-framework."*

---

### G — Format and Render Check (target publishing format)

Open the candidate in the target publishing format (PDF, epub, Word, InDesign, or whatever the production workflow uses).

- [ ] **G1** — The `# Appendix B` heading renders at the correct level in the book's heading hierarchy. If the format requires a different heading style for appendices, adjust the heading level only — do not change the text.
- [ ] **G2** — The `---` horizontal rule renders as a visual separator. If the format uses a different chapter-break convention, substitute the appropriate separator — do not change the surrounding text.
- [ ] **G3** — The 16-row domain table renders cleanly with aligned columns. If reformatting is needed for the target format, preserve all cell content exactly — do not shorten or paraphrase any scope qualifier.

---

## Pass / Fail Criteria

| Item | PASS | NEEDS FIX |
|------|------|-----------|
| A1 — URL is correct | URL matches `https://github.com/yosiwizman/cto-build-framework` exactly | URL is missing, wrong, or still shows `[URL]` |
| A2 — URL sentence reads naturally | Sentence flows without awkwardness | Sentence is broken or the URL disrupts readability |
| A3 — No residual `[URL]` placeholder | Zero occurrences of `[URL]` in the document | Any occurrence of `[URL]` found |
| B1 — Clean closing sentence | Book ends cleanly at "That position is yours. You've earned it." | Sentence is cut off or has trailing characters |
| B2 — Visual separator present | `---` rule or equivalent creates a clear break | No separator, or separator is missing/collapsed |
| B3 — Appendix heading appears once | Exactly one `# Appendix B — Domain Validation Status` heading | Heading missing, duplicated, or in wrong location |
| C1 — PARTIAL disclosure present | Paragraph beginning "Important disclosure..." is present | Paragraph is missing or shortened |
| C2 — PARTIAL disclosure positioned well | Paragraph precedes the domain table | Paragraph is buried at the end or follows the table |
| D1 — 16 rows present | All 16 domain rows are in the table | Any row is missing |
| D2 — Table is legible | Three columns are clearly separated and readable | Table is collapsed, merged, or unreadable |
| D3 — Narrow scope qualifiers intact | All three narrow qualifiers are present verbatim | Any qualifier has been shortened or softened |
| D4 — No silent Untested upgrades | All 10 Untested rows show "Untested" | Any Untested row shows a different status |
| E1 — Proof boundary section reads naturally | Section makes plain-English sense | Section is confusing or reads as a non-sequitur |
| E2 — URL in proof boundary section | URL present and correct | URL missing or wrong |
| F1 — "Does Not Show" bullets read clearly | Three bullets are clear and scannable | Bullets are confusing or broken |
| F2 — Closing URL line reads naturally | Final line is present and correct | Final line is missing or URL is wrong |
| G1 — Heading level correct | Appendix heading renders at the right level for the format | Heading level is wrong for the publishing format |
| G2 — Separator renders | `---` or equivalent renders as a visual break | Separator is absent or renders as raw text |
| G3 — Table renders cleanly | Table is legible in the target format | Table is broken or columns are misaligned |

**Decision rule:** All items must be PASS before the candidate is treated as the final submission draft. Any NEEDS FIX item must be resolved first — see Final Handoff Instruction below.

---

## What the Human Must NOT Change Without Reopening SSOT Review

The following are non-negotiable. Any change to these items requires updating the repo SSOT, re-running the publication control chain, and regenerating the candidate — before using the changed file for submission.

### 1 — Domain statuses

The five Validated, one Partially Validated, and ten Untested statuses in the domain table must not be changed. These reflect the current evidence state. Changing a status without corresponding evidence artifacts would misrepresent the framework's validation program.

### 2 — Scope qualifiers (exact wording)

These three qualifiers must remain verbatim in the domain table:

- **Search / Filtering:** "Name/company search and single category filter proven; Pilot 2 contact manager only; in-memory/localStorage; server-side search, faceted search, and pagination not tested"
- **Form Validation:** "Client-side email format validation only (one field, one rule); no other field types; no required-field enforcement beyond email; no server-side validation tested"
- **Responsive UI:** "Founder-verified on desktop and mobile; device names, OS, and browser not recorded; physical device re-execution outstanding"

Softening these qualifiers would create a mismatch between the published manuscript and the live repo SSOT.

### 3 — PARTIAL verdict disclosure

The paragraph beginning "Important disclosure: All five Validated domains have PARTIAL reviewer verdicts..." must remain in Appendix B, unshortened and unremoved. This is the honest statement of the current evidence state. Its removal would misrepresent the framework's validation status.

### 4 — Narrow validated scope

The five validated domains are validated within explicit, narrow scope boundaries. No revision may expand these boundaries in wording or implication (e.g., from "email format validation" to "form validation," or from "Pilot 2 contact manager" to "client-side search generally") without new evidence and a repo SSOT update.

### 5 — Proof-boundary caveats in "What This Table Does Not Show"

The three bullets in "What This Table Does Not Show" apply the book's own evidence discipline to the appendix. They must not be removed or softened. In particular, the caveat that "Validated" does not mean proven universally must remain.

### 6 — Distinction between tool-based proof and physical-device proof

The Responsive UI scope qualifier states that "device names, OS, and browser not recorded; physical device re-execution outstanding." This distinction — that Playwright headless verification is not the same as physical-device verification — is documented in the repo SSOT (`governance/llm-operating-discipline.md` Section 8). No revision may remove this distinction or replace it with language that implies physical-device verification has been completed.

---

## Final Handoff Instruction

### If all checklist items PASS

The candidate manuscript is cleared for use as the final submission draft.

Take the following steps in order:

1. Make the explicit owner decision: rename or promote `ASSEMBLED_MANUSCRIPT_COMPLETE_APPENDIX_B_CANDIDATE.md` as the final submission file, or copy its content into the production manuscript workflow. This is an editorial governance decision, not a repo action.
2. Before final submission, read through the five specific manuscript chapters identified in `validation/publication-readiness-checklist.md` items 3.1, 3.2, 2.5, 2.10–2.11, and 2.1–2.12 (Ch.6, Ch.8-9, Ch.11, Ch.12, Ch.13). These chapters were not addressed in the current repo work and require a human editorial read before submission.
3. Review any marketing or promotional copy derived from the manuscript against `validation/evidence-coverage-matrix.md` before launch (checklist item 7.2).

### If any checklist item NEEDS FIX — formatting or layout only (items G1–G3)

Fix the formatting in the target publishing format only. Permitted adjustments:
- Adjust the `# Appendix B` heading level to match the format's appendix heading style — do not change the heading text.
- Substitute the `---` horizontal rule with the format's chapter-break convention — do not change the surrounding text.
- Reformat the domain table for the target format (e.g., column widths, font size) — preserve all cell content exactly.

None of these adjustments require a repo action. The candidate file itself does not need to be modified.

### If any checklist item NEEDS FIX — content (items A1–F2)

Stop. Do not promote the candidate to a final submission file.

Identify which item failed. The likely causes are:

| Failed item | Likely cause |
|-------------|-------------|
| A3 — residual `[URL]` | The wrong manuscript file is being reviewed (check that you are using the candidate, not the baseline) |
| C1 — PARTIAL disclosure missing | The candidate was edited after the QA review; regeneration required |
| D3 — scope qualifier softened | The candidate was edited after the QA review; regeneration required |
| D4 — Untested domain upgraded | The candidate was edited after the QA review, or the wrong file is being reviewed |
| B3 — heading missing or duplicated | Encoding or formatting issue in the candidate file |

If the candidate file was edited after the QA review date (2026-03-18), regenerate from the patch artifact (`validation/manuscript-appendix-b-insertion-patch.md`) and re-run this checklist.

If the issue is a genuine content disagreement — for example, a domain status that should be different based on new evidence — stop the publication workflow, file the new evidence in the repo, update the SSOT, and regenerate the candidate before proceeding.

Do not submit a manuscript with a failed checklist item.

---

## Maintenance Note

This checklist is a point-in-time artifact as of 2026-03-18. It must be regenerated if:

- The candidate manuscript is edited after this date
- New validation work changes domain statuses in the repo SSOT before publication
- The candidate is regenerated from an updated `validation/appendix-b-source.md`

The canonical source files for any regeneration are:
- `validation/appendix-b-source.md` — domain table source
- `validation/manuscript-appendix-b-insertion-patch.md` — exact insertion text
- `validation/manuscript-candidate-final-review.md` — QA review to re-run

---

_Created: 2026-03-18. One new repo file only. No manuscript edits. No domain status changes. No edits to domain-matrix.md, validation-ledger.md, README.md, or any other repo file._
