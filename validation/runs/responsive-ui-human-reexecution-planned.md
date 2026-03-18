# Domain Validation Run — Responsive UI (Desktop + Mobile) — Human Re-Execution

> **RUN STATUS: PLANNED — NOT YET EXECUTED**
>
> This is a protocol for future human re-execution on real physical devices.
> It has not been performed. No results exist in this file.
> The automated Playwright run (responsive-002, 2026-03-17) is recorded separately at:
> `validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md`

---

## Run Metadata

| Field | Value |
|-------|-------|
| Domain | Responsive UI (Desktop + Mobile) |
| Project | Pilot 1 — Task Tracker + Pilot 2 — Contact Manager — both re-executed in this run |
| Project Class | Standard |
| Run Date | Not yet executed — to be filled in at time of run |
| Operator | [Human operator — record name, role, and whether they are independent of the original build operator] |
| Reviewer | [To be assigned — must be independent of the run operator] |
| Run Status | **Planned** |

---

## Why This Run Exists

The existing evidence packets for Responsive UI (`validation/evidence-packets/responsive-ui-both-pilots.md`) and the documentation-level reviewer verdict (`validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md`) both identify the same gap:

- Device names, OS versions, and browser versions used during original founder verification were **never recorded**
- Screenshots from the original verification events are **not filed in this repository**
- No independent human (other than the original builder) has re-executed and verified responsive layout for either pilot

The reviewer verdict explicitly states:

> "For this domain specifically, a new controlled verification with documented environment is more valuable than filing the original screenshots alone."

This run addresses that gap by conducting a fresh, documented verification on named devices with recorded environment details. Because the original HTML files are not currently filed in this repository, this run is executed against the reconstructed versions (`reconstructed-apps/`). It produces standalone Class 3 evidence under full artifact classification rules — it does not close or modify the original pilot evidence packet.

---

## Artifact Classification

| Field | Value |
|-------|-------|
| Source Artifact Class | **Class 2 — Reconstructed Artifact** |
| Result Artifact Class | **Class 3 — New Execution Evidence from Reconstructed Source** |

**Source artifacts used in this run:**
- Task Tracker: `reconstructed-apps/task-tracker-reconstructed.html`
- Contact Manager: `reconstructed-apps/contact-manager-reconstructed.html`

**Why Class 2 source:** The original pilot HTML files (Task Tracker and Contact Manager as delivered at the end of their respective governance runs) are not filed in this repository. The only application files currently available in the repo are the reconstructed versions in `reconstructed-apps/`. These are Class 2 — Reconstructed Artifacts per the classification rules in `validation/domain-matrix.md`.

**Rule:** All artifacts filed from this run — run log, evidence packet, reviewer verdict — must declare Class 2 source / Class 3 result. This run must not be treated or cited as a Class 1-source run.

**What this means for evidence claims:** Results from this run confirm responsive layout behavior of the reconstructed versions of both applications on named devices. They cannot be used to upgrade, confirm, or close gaps in the original pilot evidence packets (`validation/evidence-packets/responsive-ui-both-pilots.md`). This run produces standalone new Class 3 evidence only.

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
| Device name / model | [e.g., MacBook Pro 14-inch, Dell XPS 15, Surface Laptop] |
| Operating system | [e.g., macOS 14.3, Windows 11 22H2] |
| Browser name | [e.g., Safari 17, Chrome 122, Firefox 123] |
| Browser version | [exact version number] |
| Screen resolution / viewport | [e.g., 1440 × 900, 1920 × 1080] |
| Git branch | [branch name at time of run — run `git branch --show-current`] |
| Commit hash at run start | [run `git log --oneline -1` and record the hash] |

**Mobile device:**

| Field | Value |
|-------|-------|
| Device name / model | [e.g., iPhone 15, Samsung Galaxy S24, Pixel 8] |
| Operating system | [e.g., iOS 17.3, Android 14] |
| Browser name | [e.g., Safari, Chrome for iOS, Chrome for Android] |
| Browser version | [exact version number] |
| Screen size / form factor | [e.g., 390 × 844, 412 × 915] |

---

## 5. Toolchain

- AI model / version: Not applicable — this is a human verification run, not a build run
- Editor / coding tool: Not applicable
- Build tool: Not applicable — both applications are pre-built; open exactly these two files in a browser:
  - Task Tracker: `reconstructed-apps/task-tracker-reconstructed.html`
  - Contact Manager: `reconstructed-apps/contact-manager-reconstructed.html`
  - To open: in your browser, go to File > Open File (or drag the file into the browser window). No server or technical setup is required.
  - **Important:** These are Class 2 reconstructed artifacts. Do not use any other HTML file. Do not search the internet for these applications. The files are inside this repository at the paths shown above.
- Test method: Manual human verification — open each file, check layout at desktop and mobile viewport, capture screenshots

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
| Application files are HTML files opened directly in a browser — no server required | Low | Open `reconstructed-apps/task-tracker-reconstructed.html` and `reconstructed-apps/contact-manager-reconstructed.html` by using File > Open in your browser or dragging the file into the browser window; record in Section 4 whether you used the file:// method or a local server |
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
| Slices completed | / 6 |
| Checks passed — Task Tracker Desktop | / 2 |
| Checks passed — Task Tracker Mobile | / 2 |
| Checks passed — Contact Manager Desktop | / 3 |
| Checks passed — Contact Manager Mobile | / 3 |
| Environment details recorded | |
| Screenshots filed | |
| Overall run verdict | |
| Unexpected findings | |

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
| TT-D-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-D-1-task-tracker-desktop-loaded.png` | (fill in at run time) |
| TT-D-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-D-2-task-tracker-desktop-list.png` | (fill in at run time) |
| TT-M-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-M-1-task-tracker-mobile-loaded.png` | (fill in at run time) |
| TT-M-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-M-2-task-tracker-mobile-list.png` | (fill in at run time) |
| CM-D-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-D-1-contact-manager-desktop-list.png` | (fill in at run time) |
| CM-D-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-D-2-contact-manager-desktop-detail.png` | (fill in at run time) |
| CM-D-3 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-D-3-contact-manager-desktop-form.png` | (fill in at run time) |
| CM-M-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-M-1-contact-manager-mobile-list.png` | (fill in at run time) |
| CM-M-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-M-2-contact-manager-mobile-detail.png` | (fill in at run time) |
| CM-M-3 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-M-3-contact-manager-mobile-form.png` | (fill in at run time) |

---

## 12. Verdict

> **Do not fill in this section until the run is performed. This section is intentionally blank.**

- [ ] Yes — all checks passed, environment details recorded, screenshots filed
- [ ] Partially — conditions apply (describe below)
- [ ] No — run failed or produced inconclusive results (describe below)

**Conditions or limits:** (fill in after run)

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
| 6 | Create a **new standalone evidence packet** for this run at `validation/evidence-packets/responsive-ui-reexecution-[DATE].md` (replace `[DATE]` with the run date in YYYY-MM-DD format — e.g., `responsive-ui-reexecution-2026-04-15.md`). Use the template at `validation/templates/evidence-packet-template.md`. This packet must declare Class 2 source / Class 3 result and must stand alone. **Do not merge into or update the original pilot evidence packet** (`validation/evidence-packets/responsive-ui-both-pilots.md`) — that file preserves the pre-reexecution historical state with acknowledged gaps. This run's evidence is independent Class 3 evidence only. | `validation/evidence-packets/responsive-ui-reexecution-[DATE].md` (new file) |
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
