# Domain Validation Run — Responsive UI (Desktop + Mobile) — Human Re-Execution

> **RUN STATUS: PLANNED — NOT YET EXECUTED**
>
> This document is a planned run protocol. No testing has occurred. No results exist. No domain status has changed.
> Do not update `validation/validation-ledger.md` or `validation/domain-matrix.md` until this run is complete and results are recorded here.

---

## Run Metadata

| Field | Value |
|-------|-------|
| Domain | Responsive UI (Desktop + Mobile) |
| Project | Task Tracker (Class 1) + Contact Manager (Class 2) — both re-executed in this run |
| Project Class | Standard |
| Run Date | **NOT YET EXECUTED — fill in when run is performed** |
| Operator | **Fill in: name of person performing the test** |
| Reviewer | Independent — must not be the original builder of either pilot application |
| Run Status | **Planned** |

---

## Why This Run Exists

The existing evidence packets for Responsive UI (`validation/evidence-packets/responsive-ui-both-pilots.md`) and the documentation-level reviewer verdict (`validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md`) both identify the same gap:

- Device names, OS versions, and browser versions used during original founder verification were **never recorded**
- Screenshots from the original verification events are **not filed in this repository**
- No independent human (other than the original builder) has re-executed and verified responsive layout for either pilot

The reviewer verdict explicitly states:

> "For this domain specifically, a new controlled verification with documented environment is more valuable than filing the original screenshots alone."

This run addresses that gap by conducting a fresh, documented verification on named devices with recorded environment details.

---

## 1. Goal

Verify that both the Task Tracker and Contact Manager applications display correct responsive layouts on at least one desktop and one mobile device, with all environment details recorded, and produce filed screenshots as evidence — closing the device-detail gap identified in the existing evidence packet.

---

## 2. Hypothesis

Both applications were built with responsive layouts as a named MUST requirement and passed their respective release gates. The expectation is that both will display correctly on desktop and mobile. The run exists to replace unrecorded assertion evidence with documented, reproducible verification evidence — not to re-litigate the original result.

---

## 3. Scope

**In scope:**
- Task Tracker — R-08: Responsive layout (desktop + mobile)
- Contact Manager — R-11: Responsive layout (desktop + mobile)
- Desktop verification: at least one desktop or laptop device with browser recorded
- Mobile verification: at least one mobile device with browser recorded
- Screenshot capture at each required state (see Section 9 — Test Protocol)

**Out of scope:**
- All other Task Tracker requirements (R-01 through R-07, R-09, R-10)
- All other Contact Manager requirements (R-01 through R-10, R-12 through R-14)
- Tablet-specific layout testing
- Cross-browser matrix testing (multiple browsers per device)
- Specific pixel-width breakpoint testing
- Accessibility compliance testing
- Any server-rendered or native mobile applications
- Any application other than Task Tracker and Contact Manager

---

## 4. Environment — REQUIRED FIELDS

> **All fields below are mandatory.** Do not complete this run without filling in every environment field. The missing device details are the primary reason this run was planned. Recording them is the primary output of this run.

**Desktop device:**

| Field | Value |
|-------|-------|
| Device name / model | **Fill in — e.g., MacBook Pro 14" (2023)** |
| Operating system | **Fill in — e.g., macOS 14.4** |
| Browser name | **Fill in — e.g., Chrome** |
| Browser version | **Fill in — e.g., 123.0.6312.86** |
| Screen resolution / viewport | **Fill in — e.g., 1440 × 900** |
| Git branch | **Fill in — e.g., master** |
| Commit hash at run start | **Fill in — run `git log --oneline -1` to get this** |

**Mobile device:**

| Field | Value |
|-------|-------|
| Device name / model | **Fill in — e.g., iPhone 15 Pro** |
| Operating system | **Fill in — e.g., iOS 17.4** |
| Browser name | **Fill in — e.g., Safari** |
| Browser version | **Fill in — e.g., 17.4** |
| Screen size / form factor | **Fill in — e.g., 6.1" display** |

---

## 5. Toolchain

- AI model / version: Not applicable — this is a human verification run, not a build run
- Editor / coding tool: Not applicable
- Build tool: Not applicable — both applications are pre-built; open the existing files directly
- Test method: Manual human verification — open each application, check layout at desktop and mobile viewport, capture screenshots

---

## 6. Slice Plan

| Slice | Description | Status | Notes |
|-------|-------------|--------|-------|
| 1 | Open Task Tracker on desktop device — verify layout | Planned | See Section 9 for exact screens |
| 2 | Open Task Tracker on mobile device — verify layout | Planned | See Section 9 for exact screens |
| 3 | Open Contact Manager on desktop device — verify layout | Planned | See Section 9 for exact screens |
| 4 | Open Contact Manager on mobile device — verify layout | Planned | See Section 9 for exact screens |
| 5 | Record all environment details (Section 4) | Planned | Must be complete before filing |
| 6 | File screenshots to `validation/screenshots/responsive-ui-reexecution/` | Planned | See Section 11 for naming convention |

---

## 7. Risks and Unknowns

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| Application files may need to be opened locally or via a server — setup method unknown | Medium | Open `index.html` directly in browser, or run a simple local server if required; record which method was used |
| Layout may have changed since original pilot if source files were modified | Low | Record commit hash (Section 4) so the exact software state is known |
| Mobile browser may not match original verification browser | Low | Record the browser used; claim is bounded to "verified on [device] with [browser]" — not to a universal mobile claim |
| Screenshots may not clearly show the responsive behavior | Low | Take full-page screenshots and note the viewport width in the screenshot filename |

---

## 8. Checkpoints

Not applicable — this is a verification run, not a build run. No code is being written. Record the commit hash at run start in Section 4 so the software state is known.

---

## 9. Test Protocol — Manual Checklist for Non-Coder Operator

> This section is written for you to follow step by step without needing technical knowledge. Each check tells you exactly what to open, what to look at, what a PASS means, and what a FAIL means. Take a screenshot for every check you perform.

---

### Task Tracker — Desktop

**Setup:** Open the Task Tracker application in your browser on a desktop or laptop. Maximize or full-screen the window.

**Check TT-D-1: Page loads and layout fits the screen**
- What to check: The full task tracker interface is visible without horizontal scrolling. Text is readable. No elements are cut off at the edges.
- Screenshot to capture: Full browser window showing the application loaded
- PASS: The page fits the screen, is readable, and does not require horizontal scrolling
- FAIL: Elements overflow off the edge, horizontal scrollbar appears, or content is cut off

**Check TT-D-2: Task list is readable and usable**
- What to check: Task items are displayed in a list. Each task is readable. The Add Task button (or form) is accessible.
- Screenshot to capture: The task list with at least one task visible, or the empty state
- PASS: List is visible, items are readable, interface is usable
- FAIL: List is misaligned, items overlap, or key controls are inaccessible

---

### Task Tracker — Mobile

**Setup:** Open the Task Tracker application in a browser on your mobile device. Use the same URL or file path as on desktop.

**Check TT-M-1: Page loads and layout fits the mobile screen**
- What to check: The full interface is visible without horizontal scrolling. Text is readable at mobile size. No elements are cut off at the edges.
- Screenshot to capture: Full mobile browser view of the application loaded
- PASS: The page fits the mobile screen, text is readable, no horizontal overflow
- FAIL: Content overflows, horizontal scrollbar appears, text is too small to read, or interface is broken

**Check TT-M-2: Task list is readable and usable on mobile**
- What to check: Tasks are visible and readable. The Add Task button (or form) is reachable without zooming.
- Screenshot to capture: The task list on mobile, showing at least one task or the empty state
- PASS: List is usable, controls are reachable, interface works at mobile size
- FAIL: Controls are too small, hidden, or unreachable; layout breaks at mobile viewport

---

### Contact Manager — Desktop

**Setup:** Open the Contact Manager application in your browser on a desktop or laptop. Maximize or full-screen the window.

**Check CM-D-1: Home / contact list page fits the screen**
- What to check: The contact list page is visible without horizontal scrolling. The navigation and search area are accessible. Text is readable.
- Screenshot to capture: Full browser window showing the contact list page
- PASS: Layout fits, is readable, and is usable without horizontal scrolling
- FAIL: Elements overflow, layout breaks, or key navigation is inaccessible

**Check CM-D-2: Contact detail page fits the screen (if a contact exists)**
- What to check: Open a contact detail page. The full contact record is visible. Navigation back to the list is accessible.
- Screenshot to capture: Full browser window showing a contact detail page
- PASS: Contact detail fits the screen, all fields visible, back navigation accessible
- FAIL: Fields overflow, truncated, or back navigation is hidden

**Check CM-D-3: Add/Edit contact form fits the screen**
- What to check: Open the Add Contact or Edit Contact form. All form fields are visible and reachable.
- Screenshot to capture: Full browser window showing the contact form
- PASS: All form fields are visible, the Save and Cancel buttons are accessible
- FAIL: Form fields overflow, buttons are inaccessible, or form is broken

---

### Contact Manager — Mobile

**Setup:** Open the Contact Manager application in a browser on your mobile device.

**Check CM-M-1: Home / contact list page fits the mobile screen**
- What to check: The contact list is visible without horizontal scrolling. Navigation is accessible. Text is readable at mobile size.
- Screenshot to capture: Full mobile view of the contact list page
- PASS: Layout fits, is readable, no horizontal overflow
- FAIL: Layout breaks, horizontal scroll required, navigation inaccessible

**Check CM-M-2: Contact detail page fits the mobile screen**
- What to check: Open a contact detail page on mobile. All fields are visible. Back navigation is accessible.
- Screenshot to capture: Full mobile view of a contact detail page
- PASS: Contact detail page displays correctly on mobile
- FAIL: Fields overflow, back navigation hidden, or page is broken

**Check CM-M-3: Add/Edit contact form fits the mobile screen**
- What to check: Open the Add Contact or Edit Contact form on mobile. All fields visible and reachable. Save and Cancel buttons accessible.
- Screenshot to capture: Full mobile view of the contact form
- PASS: Form fields and buttons are visible and usable on mobile
- FAIL: Form fields overflow, buttons hidden or unreachable, form broken on mobile

---

## 10. Result Summary

> **Do not fill in this section until the run is performed. Leave blank until execution is complete.**

| Field | Value |
|-------|-------|
| Slices completed | __ / 6 planned |
| Checks passed — Task Tracker Desktop | __ / 2 |
| Checks passed — Task Tracker Mobile | __ / 2 |
| Checks passed — Contact Manager Desktop | __ / 3 |
| Checks passed — Contact Manager Mobile | __ / 3 |
| Environment details recorded | Yes / No |
| Screenshots filed | Yes / No — location: |
| Overall run verdict | PASS / FAIL / PARTIAL — fill in after execution |
| Unexpected findings | None / (describe) |

---

## 11. Artifact Links

> **Do not fill in this section until the run is performed.**

Screenshot naming convention (use this when saving files):
- `TT-D-1-task-tracker-desktop-loaded.png`
- `TT-D-2-task-tracker-desktop-list.png`
- `TT-M-1-task-tracker-mobile-loaded.png`
- `TT-M-2-task-tracker-mobile-list.png`
- `CM-D-1-contact-manager-desktop-list.png`
- `CM-D-2-contact-manager-desktop-detail.png`
- `CM-D-3-contact-manager-desktop-form.png`
- `CM-M-1-contact-manager-mobile-list.png`
- `CM-M-2-contact-manager-mobile-detail.png`
- `CM-M-3-contact-manager-mobile-form.png`

File location: `validation/screenshots/responsive-ui-reexecution/`

| Artifact | Type | Location | Version |
|---------|------|----------|---------|
| TT-D-1 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/TT-D-1-task-tracker-desktop-loaded.png` | **Not yet filed** |
| TT-D-2 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/TT-D-2-task-tracker-desktop-list.png` | **Not yet filed** |
| TT-M-1 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/TT-M-1-task-tracker-mobile-loaded.png` | **Not yet filed** |
| TT-M-2 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/TT-M-2-task-tracker-mobile-list.png` | **Not yet filed** |
| CM-D-1 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/CM-D-1-contact-manager-desktop-list.png` | **Not yet filed** |
| CM-D-2 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/CM-D-2-contact-manager-desktop-detail.png` | **Not yet filed** |
| CM-D-3 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/CM-D-3-contact-manager-desktop-form.png` | **Not yet filed** |
| CM-M-1 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/CM-M-1-contact-manager-mobile-list.png` | **Not yet filed** |
| CM-M-2 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/CM-M-2-contact-manager-mobile-detail.png` | **Not yet filed** |
| CM-M-3 screenshot | Screenshot | `validation/screenshots/responsive-ui-reexecution/CM-M-3-contact-manager-mobile-form.png` | **Not yet filed** |

---

## 12. Verdict

> **Do not fill in this section until the run is performed. This section is intentionally blank.**

- [ ] Yes — all checks passed, environment details recorded, screenshots filed
- [ ] Partially — some checks passed, conditions apply (describe below)
- [ ] No — run failed or produced inconclusive results (describe below)

**Conditions or limits (if partial):**

---

## Post-Execution Filing Steps

After this run is complete — all checks performed, environment details recorded, screenshots taken — the following artifacts must be updated before this run closes the evidence gap:

| Step | Action | File to Update |
|------|--------|----------------|
| 1 | Fill in all blank fields in Section 4 (Environment) | This file — `validation/runs/responsive-ui-human-reexecution-planned.md` |
| 2 | Fill in Section 10 (Result Summary) | This file |
| 3 | Fill in Section 11 (Artifact Links) with actual screenshot file paths | This file |
| 4 | Fill in Section 12 (Verdict) | This file |
| 5 | File all screenshots to `validation/screenshots/responsive-ui-reexecution/` using the naming convention in Section 11 | New directory + files |
| 6 | Update `validation/evidence-packets/responsive-ui-both-pilots.md` — add filed device details to Section 5 (Founder Verification) and update Section 3 (Artifact List) to include screenshots | `validation/evidence-packets/responsive-ui-both-pilots.md` |
| 7 | File a new reviewer verdict at `validation/reviews/responsive-ui-human-reexecution-[DATE].md` — this is a human re-execution verdict, not a documentation review; it supersedes the PARTIAL documentation verdict | New file |
| 8 | Update `validation/validation-ledger.md` — update the Responsive UI backlog row for independent human re-execution from "Not started" to "Complete" and link the new run file | `validation/validation-ledger.md` |
| 9 | Update `validation/domain-matrix.md` if the new run produces evidence that warrants a status note update | `validation/domain-matrix.md` |
| 10 | Rename or annotate this file to reflect that the run is complete — e.g., copy results to `responsive-ui-human-reexecution-[DATE].md` | This file or a renamed copy |

> **Important:** Steps 8 and 9 — updating the ledger and domain matrix — must not happen until Steps 1 through 7 are complete and artifacts are filed. Do not update domain status on the basis of a planned run. Do not update the ledger row until the run is executed and evidence is on file.

---

## 13. Next Action

- [ ] Perform the run — complete all checks in Section 9
- [ ] Record all environment details in Section 4
- [ ] File screenshots to `validation/screenshots/responsive-ui-reexecution/`
- [ ] Complete Sections 10, 11, and 12
- [ ] Follow the Post-Execution Filing Steps above

**Assigned to:** Repository owner (founding operator)
**Target date:** Not set — when ready to conduct the re-execution

---

_This run protocol is part of the CTO Build Framework validation infrastructure. The run has not been performed. No results exist. Domain status has not changed. This document is a planned protocol only — it becomes evidence only after it is executed and results are recorded here._
