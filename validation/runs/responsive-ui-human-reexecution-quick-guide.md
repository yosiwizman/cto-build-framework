# Responsive UI Human Re-Execution — Quick Guide

---

## What This Guide Is

This is a practical step-by-step guide to help you perform the Responsive UI human re-execution run correctly.

**The run has not happened yet.** This guide prepares you to execute it.

No domain status changes until the run is fully executed, results are recorded from your own direct observation, and a result file is filed. Reading this guide does not count as evidence.

The full run protocol is at: `validation/runs/responsive-ui-human-reexecution-planned.md` — keep it open while you test.

---

## What You Need Before Starting

Gather all of these before you open any app:

- [ ] Task Tracker app — available to open in a browser
- [ ] Contact Manager app — available to open in a browser
- [ ] One desktop or laptop device with a browser
- [ ] One mobile device (phone) with a browser
- [ ] Ability to take screenshots on both devices
- [ ] The commit hash of the code you are testing (run `git log --oneline -1` in the repo and copy the result)
- [ ] This guide open on a separate screen or printed out

If any of these are missing, stop and get them before testing.

---

## What to Record Before Touching the Apps

Write these down before you open anything. You will need them when filing the result.

**Date:** _______________

**Your name (reviewer / operator):** _______________

**Desktop device:**

| What | Your answer |
|------|-------------|
| Device name / model | |
| Operating system | |
| OS version | |
| Browser name | |
| Browser version | |
| Screen resolution or viewport | |

**Mobile device:**

| What | Your answer |
|------|-------------|
| Device name / model | |
| Operating system | |
| OS version | |
| Browser name | |
| Browser version | |
| Screen size or form factor | |

**Commit hash being tested:** _______________

---

## Manual Test Order

Work through all four blocks in order. Do not skip ahead.

---

### Block 1 — Task Tracker on Desktop

1. Open the Task Tracker app in your desktop browser. Maximize the window.
2. Check: does the whole page fit the screen without a horizontal scrollbar?
3. Check: is the text readable without zooming?
4. Check: can you see the task list and the controls for adding a task?
5. Take a screenshot of the full browser window. Save it as: `TT-D-1-task-tracker-desktop-loaded.png`
6. Take a second screenshot showing the task list with at least one task visible (or the empty state). Save it as: `TT-D-2-task-tracker-desktop-list.png`
7. Write down: did both checks pass, or did something look wrong?

---

### Block 2 — Task Tracker on Mobile

1. Open the Task Tracker app in your mobile browser.
2. Check: does the whole page fit without horizontal scrolling?
3. Check: is the text readable at mobile size without zooming?
4. Check: can you reach the controls for adding a task without zooming or scrolling sideways?
5. Take a screenshot of the full mobile view. Save it as: `TT-M-1-task-tracker-mobile-loaded.png`
6. Take a second screenshot showing the task list. Save it as: `TT-M-2-task-tracker-mobile-list.png`
7. Write down: did both checks pass, or did something look wrong?

---

### Block 3 — Contact Manager on Desktop

1. Open the Contact Manager app in your desktop browser. Maximize the window.
2. **Contact list page** — Check: does the contact list fit without horizontal scrolling? Is the navigation accessible?
3. Take a screenshot. Save it as: `CM-D-1-contact-manager-desktop-list.png`
4. **Contact detail page** — Open a contact record. Check: does the full contact detail fit on screen? Is the back/navigation link accessible?
5. Take a screenshot. Save it as: `CM-D-2-contact-manager-desktop-detail.png`
6. **Add/Edit form** — Open the Add Contact or Edit Contact form. Check: are all form fields visible? Are the Save and Cancel buttons accessible?
7. Take a screenshot. Save it as: `CM-D-3-contact-manager-desktop-form.png`
8. Write down: did all three checks pass, or did something look wrong?

---

### Block 4 — Contact Manager on Mobile

1. Open the Contact Manager app in your mobile browser.
2. **Contact list page** — Check: does the list fit without horizontal scrolling? Is the navigation accessible?
3. Take a screenshot. Save it as: `CM-M-1-contact-manager-mobile-list.png`
4. **Contact detail page** — Open a contact record on mobile. Check: are all fields visible? Is the back link accessible?
5. Take a screenshot. Save it as: `CM-M-2-contact-manager-mobile-detail.png`
6. **Add/Edit form** — Open the Add Contact or Edit Contact form on mobile. Check: are all fields and buttons visible and reachable?
7. Take a screenshot. Save it as: `CM-M-3-contact-manager-mobile-form.png`
8. Write down: did all three checks pass, or did something look wrong?

---

## Screenshot Checklist

You should have exactly 10 screenshots when the run is done:

- [ ] `TT-D-1-task-tracker-desktop-loaded.png`
- [ ] `TT-D-2-task-tracker-desktop-list.png`
- [ ] `TT-M-1-task-tracker-mobile-loaded.png`
- [ ] `TT-M-2-task-tracker-mobile-list.png`
- [ ] `CM-D-1-contact-manager-desktop-list.png`
- [ ] `CM-D-2-contact-manager-desktop-detail.png`
- [ ] `CM-D-3-contact-manager-desktop-form.png`
- [ ] `CM-M-1-contact-manager-mobile-list.png`
- [ ] `CM-M-2-contact-manager-mobile-detail.png`
- [ ] `CM-M-3-contact-manager-mobile-form.png`

Save all screenshots to: `validation/screenshots/responsive-ui-reexecution/`

If you missed a screenshot during the run, note it — do not re-open the app and fake it after the fact.

---

## What PASS Looks Like

The layout fits the screen on both desktop and mobile. Text is readable. All key controls (task list, navigation, forms, buttons) are visible and reachable without zooming or horizontal scrolling. You can use the app normally on both devices.

---

## What FAIL Looks Like

Content overflows the screen edge and a horizontal scrollbar appears. Text is too small to read without zooming. A button or key control is hidden, cut off, or unreachable at that screen size. The layout is visually broken — columns overlap, elements stack incorrectly, or the app is not usable on that device.

If you see anything that makes you hesitate before calling it a pass — note it. Do not call it a pass when something looks off.

---

## What to Do Immediately After the Run

**Do these steps in order. Do not skip ahead.**

1. **Fill in the planned run file** with your actual observed results.
   File: `validation/runs/responsive-ui-human-reexecution-planned.md`
   Fill in: Section 4 (environment details), Section 10 (result summary), Section 11 (screenshot links), Section 12 (verdict).

2. **Copy the result template and create a completed result file.**
   Template: `validation/templates/domain-validation-result-template.md`
   Copy it to: `validation/runs/responsive-ui-result-YYYY-MM-DD.md`
   Fill every field from your own direct observation during this run.

3. **File your screenshots.**
   Move or copy all 10 screenshots to: `validation/screenshots/responsive-ui-reexecution/`

4. **Do not update `validation/validation-ledger.md` yet.**
   The ledger is updated only after a formal reviewer verdict is filed — not on the basis of your result document alone.

5. **Do not update `validation/domain-matrix.md` yet.**
   Same rule — reviewer verdict must be filed first.

6. **Do not call the run complete until your direct observations are recorded in the result file.**
   A screenshot and a filled result document are evidence. A memory of what you saw is not.

---

_This guide is part of the CTO Build Framework validation infrastructure. It is a preparation and execution aid — not a result, not evidence, and not a domain status change. The run has not occurred._
