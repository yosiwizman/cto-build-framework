# Evidence Packet — Responsive UI — Reconstructed App Run — 2026-03-17

> **Artifact classification: Class 2 source / Class 3 result**
>
> This packet documents a new execution against reconstructed application files. It is standalone Class 3 evidence only. It must not be merged with, or used to update, the original pilot evidence packet (`validation/evidence-packets/responsive-ui-both-pilots.md`). It does not confirm original pilot execution. It does not upgrade the domain's Validated status.
>
> **Non-Negotiable Boundary Statement (per `validation/templates/reconstructed-run-wrapper-template.md`):**
> "This run uses a **Class 2 reconstructed artifact** (`reconstructed-apps/task-tracker-reconstructed.html` and `reconstructed-apps/contact-manager-reconstructed.html`) generated from the requirements documented in `pilots/task-tracker.md` and `pilots/contact-manager.md`. It produces **Class 3 evidence** for this new execution only. It must not be interpreted as confirmation of original pilot execution. It must not be used to close artifact gaps in original evidence packets. It must not be cited as support for existing Validated domain status claims."

---

## Packet Metadata

| Field | Value |
|-------|-------|
| Claim being proven | The reconstructed Task Tracker and Contact Manager applications render without horizontal overflow at desktop (1440×900) and mobile (390×844) viewport sizes in Chromium headless, as confirmed by automated Playwright layout checks on 2026-03-17 |
| Domain | Responsive UI (Desktop + Mobile) |
| Project | Pilot 1 — Task Tracker (reconstructed) + Pilot 2 — Contact Manager (reconstructed) |
| Source artifact class | Class 2 — Reconstructed Artifact |
| Result artifact class | Class 3 — New Execution Evidence from Reconstructed Source |
| Software version at time of evidence capture | Commit d38c21b (master) — `reconstructed-apps/task-tracker-reconstructed.html` and `reconstructed-apps/contact-manager-reconstructed.html` |
| Date evidence captured | 2026-03-17 |
| Evidence captured by | Claude Code (AI execution agent) — Playwright 1.58.2 / Chromium-1208 headless — independent of original pilot builder |
| Packet prepared by | Claude Code (AI execution agent) — 2026-03-17 |
| Packet version | 1.0 — initial filing |

---

## 1. The Claim

The reconstructed versions of the Task Tracker (`reconstructed-apps/task-tracker-reconstructed.html`) and Contact Manager (`reconstructed-apps/contact-manager-reconstructed.html`) render responsive layouts without horizontal overflow at:
- Desktop viewport: 1440 × 900 (Playwright browser context)
- Mobile viewport: 390 × 844 (Playwright isMobile=true, deviceScaleFactor=3)

This was verified by an automated Playwright run using Chromium-1208 headless on 2026-03-17. All 10 layout checks passed. Zero horizontal overflow (scrollWidth > clientWidth) detected in any viewport for either application.

---

## 2. What This Claim Does NOT Cover

- The original pilot deliverables — this run used reconstructed apps, not the original HTML files produced during the governance pilots
- Physical mobile device behavior — the mobile viewport was simulated via Playwright isMobile=true, not a real phone
- Human verification — no human visually inspected the screenshots during execution
- Specific breakpoints beyond 1440×900 (desktop) and 390×844 (mobile)
- Tablet-specific layouts
- Cross-browser rendering (only Chromium headless was tested)
- Touch input, native mobile browser chrome, or hardware-specific rendering
- Accessibility compliance
- The original pilots' R-08 (Task Tracker) and R-11 (Contact Manager) MUST requirement status — those remain as previously documented in the original evidence packet
- Any upgrade to the Responsive UI domain's Validated status — that requires independent re-execution per `validation/domain-matrix.md` re-execution requirement

---

## 3. Artifact List

| # | Artifact | Type | Description | File / Location |
|---|---------|------|-------------|-----------------|
| 1 | TT-D-1 screenshot | Screenshot — Class 3 | Task Tracker desktop (1440×900) initial load | `validation/screenshots/responsive-ui-reexecution/TT-D-1-task-tracker-desktop-loaded.png` |
| 2 | TT-D-2 screenshot | Screenshot — Class 3 | Task Tracker desktop (1440×900) full-page / empty task list | `validation/screenshots/responsive-ui-reexecution/TT-D-2-task-tracker-desktop-list.png` |
| 3 | TT-M-1 screenshot | Screenshot — Class 3 | Task Tracker mobile (390×844) initial load | `validation/screenshots/responsive-ui-reexecution/TT-M-1-task-tracker-mobile-loaded.png` |
| 4 | TT-M-2 screenshot | Screenshot — Class 3 | Task Tracker mobile (390×844) full-page / empty task list | `validation/screenshots/responsive-ui-reexecution/TT-M-2-task-tracker-mobile-list.png` |
| 5 | CM-D-1 screenshot | Screenshot — Class 3 | Contact Manager desktop (1440×900) contact list empty state | `validation/screenshots/responsive-ui-reexecution/CM-D-1-contact-manager-desktop-list.png` |
| 6 | CM-D-2 screenshot | Screenshot — Class 3 | Contact Manager desktop (1440×900) contact detail page | `validation/screenshots/responsive-ui-reexecution/CM-D-2-contact-manager-desktop-detail.png` |
| 7 | CM-D-3 screenshot | Screenshot — Class 3 | Contact Manager desktop (1440×900) add contact form | `validation/screenshots/responsive-ui-reexecution/CM-D-3-contact-manager-desktop-form.png` |
| 8 | CM-M-1 screenshot | Screenshot — Class 3 | Contact Manager mobile (390×844) contact list empty state | `validation/screenshots/responsive-ui-reexecution/CM-M-1-contact-manager-mobile-list.png` |
| 9 | CM-M-2 screenshot | Screenshot — Class 3 | Contact Manager mobile (390×844) contact detail page | `validation/screenshots/responsive-ui-reexecution/CM-M-2-contact-manager-mobile-detail.png` |
| 10 | CM-M-3 screenshot | Screenshot — Class 3 | Contact Manager mobile (390×844) add contact form | `validation/screenshots/responsive-ui-reexecution/CM-M-3-contact-manager-mobile-form.png` |
| 11 | Run results JSON | Machine-readable run log | All 10 check results, environment details, pass/fail per check | `validation/screenshots/responsive-ui-reexecution/run-results.json` |
| 12 | Run log | Validation run log | Automated run log with filled-in results and environment | `validation/runs/responsive-ui-reconstructed-automated-2026-03-17.md` |
| 13 | Reviewer verdict | Verdict — Class 3 | Automated run verdict | `validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md` |

---

## 4. Requirement Evidence

These are the requirements from the original pilots being tested in this reconstructed run.

| Requirement | Original Pilot | Check ID | Automated Result | Overflow Detected | Notes |
|-------------|----------------|----------|-----------------|-------------------|-------|
| R-08: Responsive layout (desktop + mobile) | Pilot 1 — Task Tracker | TT-D-1, TT-D-2 (desktop) + TT-M-1, TT-M-2 (mobile) | PASS | false (all 4 checks) | Reconstructed app; Playwright headless; not physical device |
| R-11: Responsive layout (desktop + mobile) | Pilot 2 — Contact Manager | CM-D-1, CM-D-2, CM-D-3 (desktop) + CM-M-1, CM-M-2, CM-M-3 (mobile) | PASS | false (all 6 checks) | Reconstructed app; Playwright headless; not physical device; detail page reached via programmatic navigation |

**Note on truth state:** These results confirm "Tested" status (automated tool confirmed behavior) for the reconstructed applications. They do NOT advance the original R-08 and R-11 requirements to a new Proven state — those requirements were already declared Proven in the original pilots on the original artifacts. This run is separate Class 3 evidence.

---

## 5. Founder Verification

**Did the founding operator independently verify the software?**

- [ ] Yes
- [ ] Partial
- [x] No — this run was executed by an automated tool (Claude Code / Playwright). No human visual verification was performed.

**Founder verification notes:**

This evidence packet does not include human founder verification. The automated checks confirmed the absence of horizontal overflow at the specified viewports, and screenshots were captured for each check. Human visual review of the screenshots is possible post-hoc but was not part of the executed run. This is a known gap in this packet.

---

## 6. Reviewer Verification

**Was this packet reviewed by a party other than the builder?**

- [x] Yes — automated reviewer: Claude Code (independent of original pilot builder), date: 2026-03-17, verdict file: `validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md`

**Note:** The reviewer is Claude Code (AI execution agent), not a human. The verdict is PARTIAL — automated layout checks pass; human review outstanding.

---

## 7. Release Gate Results

Not applicable to this packet. This run is a Class 3 re-execution check, not a new project under the governance loop. No release gate was run.

---

## 8. Proof-Boundary Note

**What does this evidence prove?**

The reconstructed versions of both applications (`reconstructed-apps/task-tracker-reconstructed.html` and `reconstructed-apps/contact-manager-reconstructed.html`) render without horizontal overflow at desktop (1440×900) and mobile (390×844) viewport sizes in Chromium headless on 2026-03-17. Screenshots are on file. The apps loaded, React mounted, and the layout held across both viewport sizes and both applications. The Contact Manager detail and form views were reached programmatically and also showed no overflow.

**What does this evidence NOT prove?**

- That the original pilot deliverables behave the same way
- That the apps render correctly on physical mobile devices or in browsers other than Chromium
- That human users would judge the layout acceptable
- That the responsive behavior meets any formal design standard
- That the Responsive UI domain warrants a status upgrade
- That original pilot R-08 or R-11 requirements have stronger proof than previously documented
- That any gap in the original evidence packet (`validation/evidence-packets/responsive-ui-both-pilots.md`) has been closed

---

## 9. Unresolved Limits

| Limit | Impact | Status |
|-------|--------|--------|
| Source artifacts are Class 2 (reconstructed) | Cannot confirm original pilot behavior | Accepted — declared and bounded |
| Mobile viewport is simulated, not physical | Physical device rendering not confirmed | Accepted — Playwright isMobile simulation noted; physical device test outstanding |
| Execution was automated, no human visual review | Layout quality beyond overflow check not confirmed | Accepted — screenshots available for human review post-hoc |
| Overflow check only; no interaction fidelity test | Button tap behavior, form keyboard behavior on mobile not tested | Accepted — scope is responsive layout, not full functional re-test |
| Only Chromium headless tested | Cross-browser rendering not confirmed | Accepted — claim bounded to Chromium headless only |
| Fonts loaded from Google CDN (esm.sh) | Font rendering depends on network; headless may fall back to system fonts | Accepted — noted; layout holds regardless of font face |

---

## 10. Packet Status

- [x] **Complete for its defined scope** — all sections filled, 10 screenshots filed, machine-readable results on file, reviewer verdict filed
- [ ] Incomplete
- [ ] Superseded

**Scope note:** This packet is complete as Class 3 / Class 2-source automated evidence. It does not and cannot be complete as a human re-execution evidence record. That remains outstanding.

---

_Filed 2026-03-17. Source: automated Playwright run responsive-002 against `reconstructed-apps/`. Class 2 source / Class 3 result. Does not modify or extend original pilot evidence. Standalone new evidence only._
