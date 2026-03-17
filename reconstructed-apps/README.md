# Reconstructed Apps — Classification Notice

> **Read this before using these files for any validation or testing purpose.**

---

## What These Files Are

The files in this directory are **reconstructed demo applications**, created later in a working session by generating code from the documented requirements in `pilots/task-tracker.md` and `pilots/contact-manager.md`.

| File | Based on |
|------|----------|
| `task-tracker-reconstructed.html` | Requirements documented in `pilots/task-tracker.md` |
| `contact-manager-reconstructed.html` | Requirements documented in `pilots/contact-manager.md` |

---

## What These Files Are NOT

- **Not the original pilot deliverables.** The original Task Tracker and Contact Manager applications were built during the actual pilot sessions. Those files were delivered to the founding operator and are not currently filed in this repository.
- **Not canonical historical pilot evidence.** These files did not exist at the time of the original founder verification or the original release gate events.
- **Not proof of the original validation claims.** The existing domain statuses in `validation/domain-matrix.md` and `validation/validation-ledger.md` rest on the original pilots — not on these files.

---

## What This Means for Testing

Any automated or manual testing run against these reconstructed files must be recorded as a **separate reconstructed run** — not as a continuation or confirmation of the original pilot evidence.

Specifically:

- Do not use test results from these files to update the `Last Validation Run` column in `validation/validation-ledger.md` as if the original run had been re-executed
- Do not use screenshots from these files to fill the artifact gaps noted in `validation/evidence-packets/responsive-ui-both-pilots.md` without explicitly noting the source is a reconstructed build
- Do not update any domain status on the basis of testing these files alone

If you run tests against these files and want to file the results, create a new evidence packet that clearly identifies the software version as `reconstructed-[date]` and notes the distinction from the original pilot deliverables.

---

## Why They Exist

These files serve as:

- A convenience reference showing what the pilots looked like based on documented requirements
- A local asset that enables automated screenshot capture and responsive layout testing via Playwright or similar tools
- A demo / stakeholder communication aid

They are useful. They are just not historical artifacts.

---

## The Original Pilot Deliverables

The original single-file HTML applications were delivered to the founding operator during the pilot build sessions. If you have those original files, they should be filed here under their original filenames (e.g., `task-tracker-original.html`) so the evidence chain can be completed with the actual artifacts.

---

_Classification applied: 2026-03-17. These files were generated from documented requirements in `pilots/task-tracker.md` and `pilots/contact-manager.md` and have not been through the original founder verification or release gate process._
