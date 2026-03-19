# Owner Final Action Checklist

**Type:** Operator-facing execution checklist

**Purpose:** Tells the human owner exactly what to do next to complete publication. All repo-side work is done. The remaining steps are yours. This checklist is derived from existing SSOT and adds no new claims, no new statuses, and no new doctrine.

**Date:** 2026-03-18

---

## Current Final State

The repo is complete. The candidate manuscript has passed all QA checks. The CI is green. No repo work is required before you proceed.

**Candidate manuscript to use:**
`C:\Users\yosiw\Downloads\ASSEMBLED_MANUSCRIPT_COMPLETE_APPENDIX_B_CANDIDATE.md`

**Do not use the baseline:**
`C:\Users\yosiw\Downloads\ASSEMBLED_MANUSCRIPT_COMPLETE.md` — it has a missing Appendix B and a placeholder URL.

---

## Exact Next Actions — In Order

Work through these steps in sequence. Do not skip ahead.

### Step 1 — Run the human editorial spot-check

Open the candidate manuscript. Read lines 2318–2411 only (the URL sentence, the book's closing, and the full Appendix B section).

Follow the checklist at:
`validation/human-editorial-spot-check-checklist.md`

19 items across 7 sections (A–G). Each item has a PASS / NEEDS FIX criterion. Work through all 19.

- [ ] All 19 items reviewed
- [ ] Result recorded: all PASS, or identify which item NEEDS FIX

If all 19 PASS → go to Step 2.
If any A–F item NEEDS FIX → stop. See "If Anything Fails" below.
If only G items (format/layout) NEED FIX → fix formatting in your target format. No repo action needed. Then continue to Step 2.

---

### Step 2 — Format and render check in your target publishing format

Open the candidate in the format you will actually submit (PDF, epub, Word, InDesign, or equivalent).

Check these three things:

- [ ] The `# Appendix B` heading renders at the correct level for your format. Adjust the heading level only if needed — do not change the text.
- [ ] The `---` horizontal rule renders as a visual separator. Substitute your format's chapter-break convention if needed — do not change the surrounding text.
- [ ] The 16-row domain table renders cleanly with aligned columns. Reformat column widths if needed — preserve every cell exactly.

These are the only permitted formatting adjustments. Nothing else may change.

---

### Step 3 — Read five chapters before final submission

Before submitting to a publisher or printer, open the candidate and read these five chapter sections. You are confirming that the proof-boundary language survived any prior editing pass.

| Chapter | What to confirm |
|---------|----------------|
| Ch.6 — "What You Can Honestly Claim" | Section is present and unedited |
| Ch.8-9 — Commercial Release Gate | Framed as doctrine, not proven |
| Ch.11 — Multi-session and non-Standard caveats | Preserved, not softened |
| Ch.12 — Domain claims | Each domain carries its scope qualifier |
| Ch.13 — "Designed For Is Not Proven In" | Section is present and unedited |

- [ ] All five chapter sections confirmed

---

### Step 4 — Make the promotion decision

You must make an explicit decision. This is an owner call, not a repo action.

Options:
- Rename or promote the candidate as your final submission file
- Copy its content into your production manuscript workflow

Either is acceptable. What is not acceptable is treating the baseline as the submission file.

- [ ] Owner decision made: candidate promoted to final submission

---

### Step 5 — Before launch: review any marketing copy

Before publishing any external announcement, press release, or marketing copy derived from the book, review it against:
`validation/evidence-coverage-matrix.md`

Confirm that no claim in the marketing copy describes a domain as validated, proven, or field-tested unless it appears as Validated in `validation/domain-matrix.md` with the correct scope qualifier.

- [ ] Marketing copy reviewed against evidence-coverage-matrix before publication

---

## What Must Not Be Changed

The following are non-negotiable. If a human editorial read or format pass is tempted to adjust any of these, stop. Consult `validation/human-editorial-spot-check-checklist.md` Section "What the Human Must NOT Change."

**Domain statuses.** The five Validated, one Partially Validated, and ten Untested statuses in the Appendix B table must not be changed. They reflect the current evidence state, not editorial preference.

**Narrow scope qualifiers.** These three qualifiers must remain verbatim in the domain table:
- Search / Filtering: *"Pilot 2 contact manager only; in-memory/localStorage; server-side search, faceted search, and pagination not tested"*
- Form Validation: *"one field, one rule"* and *"no server-side validation tested"*
- Responsive UI: *"device names, OS, and browser not recorded; physical device re-execution outstanding"*

**PARTIAL verdict disclosure.** The paragraph beginning "Important disclosure: All five Validated domains have PARTIAL reviewer verdicts..." must remain in Appendix B, unshortened and unremoved.

**Proof-boundary caveats.** The three bullets in "What This Table Does Not Show" must not be removed or softened.

**Tool-proof vs physical-device-proof distinction.** The Responsive UI qualifier explicitly states that device details were not recorded and physical device re-execution is outstanding. No revision may imply that physical-device verification has been completed.

Any change to the above requires updating the repo SSOT first. The manuscript follows the repo — not the other way around.

---

## Promotion Decision Rule

Promote the candidate to final submission status when:

1. All 19 items in `validation/human-editorial-spot-check-checklist.md` have passed (or G-only items are resolved by formatting adjustments only)
2. The five chapters have been read and confirmed
3. The format/render check is complete
4. You have made the explicit owner decision

Do not submit without completing all four.

---

## If Anything Fails

**If a checklist item A–F NEEDS FIX:**
First confirm you are using the candidate, not the baseline. If the candidate was edited after 2026-03-18, it must be regenerated. Instructions at: `validation/manuscript-appendix-b-insertion-patch.md`

**If a domain status seems wrong to you:**
Do not edit the manuscript. The statuses reflect the actual evidence. Any change requires new validation work. Process at: `validation/evidence-expansion-roadmap.md`

**If you are unsure which file to use:**
Read: `validation/project-closeout-index.md` — Section 7 (Restart Instructions) and Section 3 (Canonical Artifact Map)

**If the CI workflow fails after any future repo change:**
Read: `.github/workflows/ssot-integrity.yml` inline comments for the exclusion list pattern.

---

## Exact File Paths

| What you need | Path |
|---------------|------|
| Candidate manuscript (use this) | `C:\Users\yosiw\Downloads\ASSEMBLED_MANUSCRIPT_COMPLETE_APPENDIX_B_CANDIDATE.md` |
| Baseline manuscript (do not submit) | `C:\Users\yosiw\Downloads\ASSEMBLED_MANUSCRIPT_COMPLETE.md` |
| Human editorial spot-check checklist | `C:\Users\yosiw\cto-build-framework\validation\human-editorial-spot-check-checklist.md` |
| Release readiness decision | `C:\Users\yosiw\cto-build-framework\validation\release-readiness-decision.md` |
| Publication readiness checklist | `C:\Users\yosiw\cto-build-framework\validation\publication-readiness-checklist.md` |
| Appendix B source (regeneration input) | `C:\Users\yosiw\cto-build-framework\validation\appendix-b-source.md` |
| Insertion patch (regeneration instructions) | `C:\Users\yosiw\cto-build-framework\validation\manuscript-appendix-b-insertion-patch.md` |
| Evidence coverage matrix (marketing copy gate) | `C:\Users\yosiw\cto-build-framework\validation\evidence-coverage-matrix.md` |
| Future validation roadmap | `C:\Users\yosiw\cto-build-framework\validation\evidence-expansion-roadmap.md` |
| Repo closeout entrypoint | `C:\Users\yosiw\cto-build-framework\validation\project-closeout-index.md` |

---

_Created: 2026-03-18. One new repo file only. No manuscript edits. No domain status changes. No edits to any existing repo file._
