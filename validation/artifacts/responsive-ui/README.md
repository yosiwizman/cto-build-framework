# Responsive UI — Screenshot Evidence Folder

---

## Purpose

This folder is the canonical location for screenshots captured during the Responsive UI human re-execution run.

**Screenshots alone do not change validation status.** Placing files here is one step in the evidence chain — not the final step. The formal result artifact and reviewer verdict must also be filed before any status changes.

---

## Save Location Rule

All screenshots captured during the Responsive UI re-execution run go in this folder:

`validation/artifacts/responsive-ui/`

Do not save them to your desktop and link them later. Save them here directly so the evidence is in the repo.

---

## Required Filenames

Save each screenshot with the exact filename listed below. These names match the live capture sheet and the planned run protocol.

| # | Filename | What to capture |
|---|----------|-----------------|
| 01 | `01-task-tracker-desktop-home.png` | Task Tracker loaded on desktop — full browser window |
| 02 | `02-task-tracker-desktop-add-task.png` | Add task form or input visible on desktop |
| 03 | `03-task-tracker-desktop-task-list.png` | Task list with at least one task on desktop |
| 04 | `04-task-tracker-mobile-home.png` | Task Tracker loaded on mobile — full screen |
| 05 | `05-task-tracker-mobile-add-task.png` | Add task form or input visible on mobile |
| 06 | `06-task-tracker-mobile-task-list.png` | Task list with at least one task on mobile |
| 07 | `07-contact-manager-desktop-home.png` | Contact Manager home / contact list on desktop |
| 08 | `08-contact-manager-desktop-add-contact.png` | Add contact form on desktop |
| 09 | `09-contact-manager-desktop-contact-list.png` | Contact list populated on desktop |
| 10 | `10-contact-manager-desktop-contact-details.png` | Contact detail page on desktop |
| 11 | `11-contact-manager-mobile-home.png` | Contact Manager home / contact list on mobile |
| 12 | `12-contact-manager-mobile-add-contact.png` | Add contact form on mobile |
| 13 | `13-contact-manager-mobile-contact-list.png` | Contact list populated on mobile |
| 14 | `14-contact-manager-mobile-contact-details.png` | Contact detail page on mobile |

---

## Screenshot Rules

- Capture exactly what is visible on screen during the test — do not crop, annotate, or edit before filing
- Do not rename files casually — the filenames above match the live capture sheet and run protocol; changing them breaks the evidence trail
- If a required screenshot cannot be captured during the run, note it in `validation/runs/responsive-ui-live-capture-sheet.md` under the screenshot checklist — do not leave it silently missing
- If a failure occurs and you need an additional screenshot to document it, use this naming convention:

```
fail-01-short-description.png
fail-02-short-description.png
```

---

## After Capture

Once your screenshots are saved here:

1. Confirm all required files exist in this folder before proceeding
2. Return to `validation/runs/responsive-ui-live-capture-sheet.md` and check off each screenshot
3. Copy `validation/templates/domain-validation-result-template.md` to `validation/runs/responsive-ui-result-YYYY-MM-DD.md` and fill it from your direct observations
4. File the completed result document

**Do not update `validation/validation-ledger.md` or `validation/domain-matrix.md` until the formal evidence chain is complete** — result document filed, screenshots in this folder, and a reviewer verdict issued. Screenshots in this folder are one input to that chain, not the conclusion of it.

---

_This folder is part of the CTO Build Framework validation infrastructure. No screenshots are present yet — the run has not been executed._
