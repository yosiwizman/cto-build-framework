# Reconstructed Run Wrapper

> **Instructions:** Copy this file to `validation/runs/{domain}-reconstructed-run-{date}.md` before beginning any validation run that uses a file from `reconstructed-apps/`. Fill every required field before recording results. Do not create this file after the run — it must be filled at the start so the classification is declared upfront, not retrospectively.

---

## Purpose

This wrapper exists for one reason: to isolate testing against reconstructed artifacts from the original pilot evidence chain.

Files in `reconstructed-apps/` are Class 2 artifacts — generated later from documented requirements, not produced during the original pilot sessions. Any testing against them produces Class 3 evidence for this new execution only. That evidence is independent, separately scoped, and must never be merged with or treated as confirmation of the original pilot runs.

This template enforces that boundary at the point of execution. If you are testing a file from `reconstructed-apps/`, you must use this wrapper. If you are testing an original pilot deliverable, use `validation/templates/domain-validation-run-template.md` instead.

---

## Source Classification

> **All fields are required. Do not proceed to execution until this section is complete.**

| Field | Value |
|-------|-------|
| Source Artifact Class | Class 2 — Reconstructed Artifact |
| Source Artifact Path | (exact path, e.g., `reconstructed-apps/task-tracker-reconstructed.html`) |
| Reconstructed Artifact Name | (filename, e.g., `task-tracker-reconstructed.html`) |
| Original Pilot Referenced | (name of the pilot this artifact was reconstructed from, e.g., `Task Tracker — Class 1 pilot`) |
| Run Classification | Class 3 — New Execution Evidence from Reconstructed Source |
| Execution Date | YYYY-MM-DD |

---

## Non-Negotiable Boundary Statement

> **Copy this statement into the completed run artifact and fill in the blanks. Do not paraphrase or abbreviate it.**

"This run uses a **Class 2 reconstructed artifact** (`[source artifact path]`) generated from the requirements documented in `[source pilot doc]`. It produces **Class 3 evidence** for this new execution only. It must not be interpreted as confirmation of original pilot execution. It must not be used to close artifact gaps in original evidence packets. It must not be cited as support for existing Validated domain status claims."

---

## Allowed Claims

Results from this run MAY support:

- **New behavioral observations** — what the reconstructed artifact does when tested in a defined environment
- **Responsive layout behavior** — what the layout looks like at specific viewport sizes on specific devices, as a Class 3 finding
- **Automated screenshot capture** — screenshots filed as Class 3 artifacts under their own dated label
- **Secondary test coverage** — documented evidence that a reconstructed build meets the requirements it was generated from, filed independently
- **Future domain expansion** — if a new domain (not previously validated) is being tested for the first time against a reconstructed artifact, and the run produces a full independent artifact trail
- **Process validation** — confirming that the governance toolchain (Playwright scripts, run protocols, result templates) works correctly

---

## Forbidden Claims

Results from this run MUST NOT support:

- **Closing original artifact gaps** — a screenshot from this run does not fill the missing screenshots referenced in `validation/evidence-packets/responsive-ui-both-pilots.md` or any other original evidence packet
- **Confirming original pilot execution** — this run does not re-execute or re-confirm what the founding operator verified during the original pilots
- **Upgrading existing domain status** — Validated domains were validated on original execution evidence; this run cannot strengthen or extend those claims
- **Replacing original pilot deliverables** — the reconstructed artifact is not the original file and cannot substitute for it in any historical evidence claim
- **Appending results to original evidence packets** — do not add screenshots, checks, or verdict notes from this run to any file in `validation/evidence-packets/` that documents original pilot evidence
- **Cross-class validation claims** — do not combine Class 1 and Class 2 source evidence in a single claim or verdict

---

## Execution Context

| Field | Value |
|-------|-------|
| Execution type | Human / Automated (Playwright) / Mixed |
| Tool used | (e.g., Playwright 1.58.2, Chrome manual review, Safari manual review) |
| Device — desktop | (name, OS, OS version, browser, browser version, viewport) |
| Device — mobile | (name, OS, OS version, browser, browser version, screen size) |
| Repo commit hash at run start | (run `git log --oneline -1` and paste result) |
| Reviewer / operator name | |
| Reviewer independence | Confirmed independent — not the original pilot builder / Not independent — note limitation |

---

## Artifact Outputs

Check each item off as it is produced. Do not file incomplete artifacts.

**During the run:**
- [ ] Run log — filed to `validation/runs/{domain}-reconstructed-run-{date}.md` (this file)
- [ ] Screenshots — filed to `validation/artifacts/reconstructed-runs/{domain}-{date}/` using consistent naming
- [ ] Failure log — any failures observed documented inline or in a separate file

**After the run:**
- [ ] Result artifact — created from `validation/templates/domain-validation-result-template.md`, saved as `validation/runs/{domain}-reconstructed-result-{date}.md`; Artifact Provenance section must declare Class 2 source and Class 3 result
- [ ] Reviewer verdict — created from `validation/templates/reviewer-verdict-template.md`, saved as `validation/reviews/{domain}-reconstructed-review-{date}.md`; must not be merged with any original pilot reviewer verdict
- [ ] Evidence packet (Class 3 only) — if this run is intended to produce a standing new evidence record, create a new packet in `validation/evidence-packets/{domain}-reconstructed-{date}.md`; must be clearly labeled as a Class 3 reconstructed-source packet

**Naming rule:** All artifacts produced by this run must include `-reconstructed-` in their filename. This prevents silent conflation with original pilot artifacts in any directory listing.

---

## Filing Rules

1. **Do not save to existing evidence packet files** — create new files only
2. **Do not save screenshots to `validation/artifacts/responsive-ui/`** if that folder is reserved for original pilot screenshots — use a separate dated subfolder: `validation/artifacts/reconstructed-runs/{domain}-{date}/`
3. **Label every produced file** with `-reconstructed-{date}` in the filename
4. **Do not update `validation/validation-ledger.md` domain status columns** on the basis of this run — ledger status updates require Class 1 or Class 3 evidence from original or new pilot execution, not reconstructed-source runs, unless a new domain is being independently validated for the first time
5. **Do not update `validation/domain-matrix.md` status rows** without a reviewer verdict filed under the Class 3 filing rules above
6. **Record artifact class in every filed document** — every file produced by this run must state "Class 2 source artifact / Class 3 result" in its metadata or provenance section

---

## Reviewer Gate

Before accepting any result from this run, a reviewer must confirm all of the following:

- [ ] The Source Classification section above is fully filled in
- [ ] The Non-Negotiable Boundary Statement is present in the run log and completed result artifact
- [ ] All produced artifacts include `-reconstructed-` in their filenames
- [ ] No results from this run have been appended to original evidence packet files
- [ ] The result artifact's Artifact Provenance section (from `domain-validation-result-template.md`) declares Class 2 source and Class 3 result
- [ ] The reviewer verdict (when filed) is saved as a separate file from any original pilot reviewer verdict
- [ ] No domain status row in `validation/domain-matrix.md` has been changed on the basis of this run without a full independent Class 3 artifact trail

If any box above cannot be checked, do not accept the result. Return to the operator and request the missing item.

---

## Final Warning

**Reconstructed testing cannot close gaps in original pilot evidence packets.**

The evidence gaps acknowledged in `validation/evidence-packets/responsive-ui-both-pilots.md` — and in the corresponding reviewer verdict at `validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md` — reflect the absence of original founder verification artifacts. Screenshots, layout checks, and test results produced from a reconstructed build do not fill those gaps. They are new evidence about a new artifact. They are useful. They are just not the same thing.

The original gaps remain open until original artifacts are recovered or a new Class 3 run with full independent certification produces evidence that explicitly supersedes the original claims — not a reconstructed-source run that approximates them.

---

_This template is part of the CTO Build Framework validation infrastructure. Do not modify the template itself — copy it for each reconstructed run. The classification rules enforced here are defined in `validation/domain-matrix.md` — Artifact Classification._
