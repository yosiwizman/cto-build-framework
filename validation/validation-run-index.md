# Validation Run Index

**Canonical registry of all validation runs across the CTO Build Framework.**

Every run — planned, in progress, or completed — must be registered here. This index enables traceability from execution through result, evidence packet, and reviewer verdict to domain status.

---

## Purpose

This file is the single source of truth for what validation runs exist, what artifact class they use, and where their outputs are filed.

It is not a status file. Domain status lives in `validation/domain-matrix.md`. This index tracks the execution record that feeds into that status — not the status itself.

**This index enables:**
- Audit traceability: run → result → evidence → domain status
- Artifact class enforcement: every run's class is declared at registration
- Gap visibility: planned runs with no results are immediately visible
- Reviewer orientation: reviewers can locate every artifact from one place

**This index does not replace:**
- `validation/domain-matrix.md` — domain status and classification definitions
- `validation/validation-ledger.md` — high-level domain evidence status
- Individual run files — the actual execution records

---

## Index Table

| Run ID | Domain | Run Type | Artifact Class | Source Artifact | Run File | Result File | Evidence Packet | Reviewer Verdict | Status | Notes |
|--------|--------|----------|----------------|-----------------|----------|-------------|-----------------|-----------------|--------|-------|
| crud-001 | CRUD / Local-State | Original pilot | Class 1 | Task Tracker HTML (not in repo — pre-template) | None on file — predates run template | None on file | `validation/evidence-packets/task-tracker-client-side-crud.md` | `validation/reviews/crud-local-state-task-tracker-review-2026-03-16.md` — PARTIAL | Completed (pre-template) | Original pilot run; evidence formalized 2026-03-16; no run log file; screenshots not in repo |
| multipage-001 | Client-Side Multi-Page Apps | Original pilot | Class 1 | Contact Manager HTML (not in repo — pre-template) | None on file — predates run template | None on file | `validation/evidence-packets/contact-manager-client-side-multipage.md` | `validation/reviews/client-side-multipage-contact-manager-review-2026-03-16.md` — PARTIAL | Completed (pre-template) | Original pilot run; evidence formalized 2026-03-16; no run log file; screenshots not in repo |
| search-001 | Search / Filtering | Original pilot | Class 1 | Contact Manager HTML (not in repo — pre-template) | None on file — predates run template | None on file | `validation/evidence-packets/contact-manager-search-filtering.md` | `validation/reviews/search-filtering-contact-manager-review-2026-03-16.md` — PARTIAL | Completed (pre-template) | Sub-domain of contact-manager pilot; R-05 and R-06 only; no run log file |
| formval-001 | Form Validation | Original pilot | Class 1 | Contact Manager HTML (not in repo — pre-template) | None on file — predates run template | None on file | `validation/evidence-packets/contact-manager-form-validation.md` | `validation/reviews/form-validation-contact-manager-review-2026-03-16.md` — PARTIAL | Completed (pre-template) | Sub-domain of contact-manager pilot; R-09 only (email format); no run log file |
| responsive-001 | Responsive UI | Original pilot | Class 1 | Task Tracker + Contact Manager HTML (not in repo — pre-template) | None on file — predates run template | None on file | `validation/evidence-packets/responsive-ui-both-pilots.md` | `validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md` — PARTIAL | Completed (pre-template) | Cross-pilot domain; R-08 (Task Tracker) + R-11 (Contact Manager); device details not recorded |
| responsive-002 | Responsive UI | Automated Playwright run (not human re-execution) | **Class 2 source / Class 3 result** | `reconstructed-apps/task-tracker-reconstructed.html` + `reconstructed-apps/contact-manager-reconstructed.html` | `validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md` | `validation/screenshots/responsive-ui-reexecution/run-results.json` | `validation/evidence-packets/responsive-ui-reconstructed-2026-03-17.md` | `validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md` — PARTIAL — automated tool run; human re-execution outstanding | **Completed — PARTIAL** | Executed 2026-03-17 by Claude Code / Playwright 1.58.2 / Chromium-1208 headless; 10/10 layout checks PASS; zero horizontal overflow; Class 2 source confirmed; original HTML files not in repo; human physical device verification outstanding; domain status unchanged |

---

## How to Register a New Run

Before beginning any validation run:

1. Choose a Run ID using the format `{domain-short}-{sequence}` (e.g., `auth-001`, `responsive-003`)
2. Add a row to this table with at minimum: Run ID, Domain, Run Type, Artifact Class, Source Artifact, Run File path
3. Set Status to `planned`
4. Commit the index update before beginning execution — the registration must predate the run, not follow it

After the run:

5. Fill in Result File path (when result artifact is created)
6. Fill in Evidence Packet path (when packet is filed)
7. Fill in Reviewer Verdict path (when verdict is filed)
8. Update Status to `completed` or `rejected`
9. Commit the index update in the same commit as the filed artifacts

---

## Rules

| Rule | Detail |
|------|--------|
| Register before executing | Every run must have an index row before execution begins — post-hoc registration is not accepted |
| Run IDs must be unique | No two rows may share the same Run ID — increment the sequence number for each new run in a domain |
| Artifact class must match run template | The class declared here must match the class declared in the run file's Artifact Classification section |
| Class 2 source runs must use the wrapper | Any run against a file in `reconstructed-apps/` must use `validation/templates/reconstructed-run-wrapper-template.md` and be registered here with Artifact Class = Class 2 source / Class 3 result |
| Result and evidence paths filled on completion | Leave these blank at registration — fill them only when the artifact is actually filed, not when planned |
| No domain status change without a complete row | A domain status change in `validation/domain-matrix.md` requires a completed row here with Run File, Result File, Evidence Packet, and Reviewer Verdict all linked |
| PARTIAL verdicts do not close the run | A PARTIAL reviewer verdict means the run is completed but the evidence chain is incomplete — note the gap in Notes |
| Pre-template runs are registered with gaps acknowledged | The five original pilot runs above predate this system; they are registered honestly with "None on file" where artifacts are missing |

---

## Example: Registering a Future Reconstructed Run

The row below shows what a correctly registered Class 2 / Class 3 run looks like. This is an example only — it is not a real run.

| Run ID | Domain | Run Type | Artifact Class | Source Artifact | Run File | Result File | Evidence Packet | Reviewer Verdict | Status | Notes |
|--------|--------|----------|----------------|-----------------|----------|-------------|-----------------|-----------------|--------|-------|
| responsive-003 | Responsive UI | Reconstructed run | Class 2 source / Class 3 result | `reconstructed-apps/task-tracker-reconstructed.html` | `validation/runs/responsive-ui-reconstructed-run-2026-XX-XX.md` | `validation/runs/responsive-ui-reconstructed-result-2026-XX-XX.md` | `validation/evidence-packets/responsive-ui-reconstructed-2026-XX-XX.md` (if filed) | `validation/reviews/responsive-ui-reconstructed-review-2026-XX-XX.md` | Planned | Must use reconstructed-run-wrapper-template.md; cannot close gaps in responsive-001 evidence packet |

---

## Traceability Map

For any run in this index, the full chain must be resolvable:

```
Run ID
  └── Run File (execution record + artifact class declaration)
        └── Result File (direct observations from the run)
              └── Evidence Packet (structured proof record)
                    └── Reviewer Verdict (independent assessment)
                          └── domain-matrix.md status (if verdict supports update)
```

A break anywhere in this chain means the chain is incomplete. The Notes column must record the break explicitly. Incomplete chains do not block domain status from remaining as-is — they block domain status from being upgraded.

---

_Last updated: 2026-03-17. Maintained as a living document — updated only when a run is registered or its artifacts are filed. Do not update to reflect planned work that has not been committed to a run file._
