# Responsive UI Human Re-Execution — Live Capture Sheet

---

## Purpose

This is your live note-taking sheet. Fill it in while you are performing the Responsive UI human re-execution run.

**Filling this sheet does not count as proof by itself.** After the run is done, you will use the information here to fill the formal result artifact (`validation/templates/domain-validation-result-template.md`). That formal file — with screenshots attached — is the actual evidence record.

Keep this sheet open alongside `validation/runs/responsive-ui-human-reexecution-quick-guide.md` during testing.

---

## Environment Capture

Fill this in before you open any app. Do not skip these fields — they are the primary gap this run is closing.

| Field | Your answer |
|-------|-------------|
| Date | |
| Tester name | |
| Commit hash (run `git log --oneline -1`) | |
| Desktop — device name / model | |
| Desktop — OS | |
| Desktop — OS version | |
| Desktop — browser | |
| Desktop — browser version | |
| Desktop — viewport / screen resolution | |
| Mobile — device name / model | |
| Mobile — OS | |
| Mobile — OS version | |
| Mobile — browser | |
| Mobile — browser version | |
| Mobile — viewport / screen size | |

---

## Task Tracker Checks

Open Task Tracker. Work through desktop first, then mobile.

| # | Check | Result | Notes |
|---|-------|--------|-------|
| TT-1 | App loads on desktop without error | PASS / FAIL | |
| TT-2 | App loads on mobile without error | PASS / FAIL | |
| TT-3 | Layout fits desktop screen — no horizontal scrollbar | PASS / FAIL | |
| TT-4 | Layout fits mobile screen — no horizontal scrollbar | PASS / FAIL | |
| TT-5 | Controls (add task, task list) are visible and readable on desktop | PASS / FAIL | |
| TT-6 | Controls (add task, task list) are visible and readable on mobile | PASS / FAIL | |
| TT-7 | No overlapping, clipped, or broken elements observed on desktop | PASS / FAIL | |
| TT-8 | No overlapping, clipped, or broken elements observed on mobile | PASS / FAIL | |

---

## Contact Manager Checks

Open Contact Manager. Work through desktop first, then mobile.

| # | Check | Result | Notes |
|---|-------|--------|-------|
| CM-1 | App loads on desktop without error | PASS / FAIL | |
| CM-2 | App loads on mobile without error | PASS / FAIL | |
| CM-3 | Layout fits desktop screen — no horizontal scrollbar | PASS / FAIL | |
| CM-4 | Layout fits mobile screen — no horizontal scrollbar | PASS / FAIL | |
| CM-5 | Navigation (between list, detail, form) remains usable on desktop | PASS / FAIL | |
| CM-6 | Navigation (between list, detail, form) remains usable on mobile | PASS / FAIL | |
| CM-7 | Contact list is readable and usable on desktop | PASS / FAIL | |
| CM-8 | Contact list is readable and usable on mobile | PASS / FAIL | |
| CM-9 | Add/Edit form fields and buttons are accessible on desktop | PASS / FAIL | |
| CM-10 | Add/Edit form fields and buttons are accessible on mobile | PASS / FAIL | |
| CM-11 | No overlapping, clipped, or broken elements observed on desktop | PASS / FAIL | |
| CM-12 | No overlapping, clipped, or broken elements observed on mobile | PASS / FAIL | |

---

## Screenshot Checklist

Take each screenshot as you reach that point in the test. Check it off immediately after capturing it.

**Task Tracker:**
- [ ] `TT-D-1-task-tracker-desktop-loaded.png` — full desktop browser window, app loaded
- [ ] `TT-D-2-task-tracker-desktop-list.png` — task list visible on desktop
- [ ] `TT-M-1-task-tracker-mobile-loaded.png` — full mobile view, app loaded
- [ ] `TT-M-2-task-tracker-mobile-list.png` — task list visible on mobile

**Contact Manager:**
- [ ] `CM-D-1-contact-manager-desktop-list.png` — contact list page on desktop
- [ ] `CM-D-2-contact-manager-desktop-detail.png` — contact detail page on desktop
- [ ] `CM-D-3-contact-manager-desktop-form.png` — add/edit form on desktop
- [ ] `CM-M-1-contact-manager-mobile-list.png` — contact list page on mobile
- [ ] `CM-M-2-contact-manager-mobile-detail.png` — contact detail page on mobile
- [ ] `CM-M-3-contact-manager-mobile-form.png` — add/edit form on mobile

Save all screenshots to: `validation/screenshots/responsive-ui-reexecution/`

---

## Failure Log

Use a row for each issue you observe. Leave blank if no failures occurred.

| ID | App | Device | Screen / Route | What failed | Screenshot filename |
|----|-----|--------|----------------|-------------|---------------------|
| F-1 | | | | | |
| F-2 | | | | | |
| F-3 | | | | | |

_Add rows as needed. If no failures: write "None observed" across the first row._

---

## Completion Gate

Before you close this sheet and move to the formal result artifact, confirm:

- [ ] All environment fields in the Environment Capture section are filled in
- [ ] All TT checks have a PASS or FAIL result recorded
- [ ] All CM checks have a PASS or FAIL result recorded
- [ ] All 10 screenshots have been taken and checked off
- [ ] Any failures are logged in the Failure Log
- [ ] Commit hash is recorded

If any of the above are unchecked, do not move to the formal result file yet — complete the missing items first or note why they cannot be completed.

**When all boxes above are checked:** copy `validation/templates/domain-validation-result-template.md` to `validation/runs/responsive-ui-result-YYYY-MM-DD.md` and transfer your observations into it. Use your direct observations from this sheet — not memory, not AI summaries.

---

_This sheet is a working note, not an evidence artifact. It becomes evidence only after the formal result file is created and screenshots are filed._
