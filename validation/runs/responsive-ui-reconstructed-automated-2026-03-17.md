# Domain Validation Run — Responsive UI — Automated Playwright Run — 2026-03-17

> **Artifact classification: Class 2 source / Class 3 result**
>
> **RUN STATUS: COMPLETED — 2026-03-17 — AUTOMATED PLAYWRIGHT RUN (NOT HUMAN RE-EXECUTION)**
>
> This run was executed on 2026-03-17 using Playwright 1.58.2 / Chromium-1208 headless by Claude Code (AI execution agent).
> This is an automated tool-based execution, not a manual human verification.
> All 10 layout checks PASSED. Zero horizontal overflow detected across all viewports.
> Artifacts filed as Class 2 source / Class 3 result. Domain status has NOT changed.
> Human physical device verification remains outstanding — see `validation/runs/responsive-ui-human-reexecution-planned.md`.

---

## Run Metadata

| Field | Value |
|-------|-------|
| Domain | Responsive UI (Desktop + Mobile) |
| Project | Pilot 1 — Task Tracker + Pilot 2 — Contact Manager — both executed in this run |
| Project Class | Standard |
| Run Date | 2026-03-17 |
| Operator | Claude Code (AI execution agent) — Playwright 1.58.2 / Chromium-1208 headless — NOT a human operator |
| Reviewer | Independent of original pilot builder — automated run; human reviewer verdict filed separately at `validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md` |
| Run Status | **Completed — Automated Tool Run — PARTIAL (human re-execution outstanding)** |

---

## Why This Run Exists

The existing evidence packets for Responsive UI (`validation/evidence-packets/responsive-ui-both-pilots.md`) and the documentation-level reviewer verdict (`validation/reviews/responsive-ui-both-pilots-review-2026-03-16.md`) both identify the same gap:

- Device names, OS versions, and browser versions used during original founder verification were **never recorded**
- Screenshots from the original verification events are **not filed in this repository**
- No independent human (other than the original builder) has re-executed and verified responsive layout for either pilot

The reviewer verdict explicitly states:

> "For this domain specifically, a new controlled verification with documented environment is more valuable than filing the original screenshots alone."

This automated run was executed to produce Class 3 evidence using a documented, reproducible tool environment. Because the original HTML files are not currently filed in this repository, this run was executed against the reconstructed versions (`reconstructed-apps/`). It produces standalone Class 3 evidence under full artifact classification rules — it does not close or modify the original pilot evidence packet.

The human re-execution protocol for this domain (manual verification on real physical devices) is maintained separately at `validation/runs/responsive-ui-human-reexecution-planned.md`.

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

**Rule:** All artifacts filed from this run — run log, evidence packet, reviewer verdict — declare Class 2 source / Class 3 result. This run must not be treated or cited as a Class 1-source run.

**What this means for evidence claims:** Results from this run confirm responsive layout behavior of the reconstructed versions of both applications in Chromium headless. They cannot be used to upgrade, confirm, or close gaps in the original pilot evidence packets (`validation/evidence-packets/responsive-ui-both-pilots.md`). This run produces standalone new Class 3 evidence only.

---

## Scope

**In scope:**
- Task Tracker — R-08: Responsive layout (desktop + mobile)
- Contact Manager — R-11: Responsive layout (desktop + mobile)
- Desktop viewport check: 1440 × 900 (Playwright viewport setting)
- Mobile viewport check: 390 × 844 (Playwright isMobile=true simulation)
- Overflow detection: scrollWidth > clientWidth check per viewport per application

**Out of scope:**
- All other Task Tracker requirements (R-01 through R-07, R-09, R-10)
- All other Contact Manager requirements (R-01 through R-10, R-12 through R-14)
- Physical mobile device testing
- Human visual layout review
- Cross-browser matrix testing (multiple browsers per device)
- Tablet-specific layout testing
- Accessibility compliance testing
- Any server-rendered or native mobile applications

---

## Environment

**Desktop device:**

| Field | Value |
|-------|-------|
| Device name / model | Windows 11 Pro — automated Playwright headless execution (not a physical device) |
| Operating system | Windows 11 Pro 10.0.26200 |
| Browser name | Chromium headless (ms-playwright/chromium-1208) |
| Browser version | Chromium 1208 — chrome-win64/chrome.exe |
| Screen resolution / viewport | 1440 × 900 (simulated — Playwright viewport setting) |
| Git branch | evidence/responsive-ui-reconstructed-run-2026-03-17 |
| Commit hash at run start | d38c21b |

**Mobile device:**

| Field | Value |
|-------|-------|
| Device name / model | Playwright isMobile=true simulation — NOT a physical mobile device |
| Operating system | Windows 11 Pro (host) — mobile simulation via Playwright deviceScaleFactor=3 |
| Browser name | Chromium headless (ms-playwright/chromium-1208) with isMobile=true |
| Browser version | Chromium 1208 |
| Screen size / form factor | 390 × 844 (simulated viewport — iPhone 14 equivalent — not a physical device) |

---

## Toolchain

- AI model / execution agent: Claude Code (claude-sonnet-4-6)
- Test tool: Playwright 1.58.2
- Browser: Chromium 1208 (ms-playwright/chromium-1208) — headless
- Source files: `reconstructed-apps/task-tracker-reconstructed.html` + `reconstructed-apps/contact-manager-reconstructed.html`
- Run script: `validation/screenshots/responsive-ui-reexecution/run-responsive-tests.js`
- Results: `validation/screenshots/responsive-ui-reexecution/run-results.json`

---

## Checks Performed

| Check ID | Application | Viewport | Overflow Detected | Result |
|----------|-------------|----------|------------------|--------|
| TT-D-1 | Task Tracker | Desktop 1440×900 | false | PASS |
| TT-D-2 | Task Tracker | Desktop 1440×900 (full-page) | false | PASS |
| TT-M-1 | Task Tracker | Mobile 390×844 | false | PASS |
| TT-M-2 | Task Tracker | Mobile 390×844 (full-page) | false | PASS |
| CM-D-1 | Contact Manager | Desktop 1440×900 (contact list) | false | PASS |
| CM-D-2 | Contact Manager | Desktop 1440×900 (contact detail) | false | PASS |
| CM-D-3 | Contact Manager | Desktop 1440×900 (add contact form) | false | PASS |
| CM-M-1 | Contact Manager | Mobile 390×844 (contact list) | false | PASS |
| CM-M-2 | Contact Manager | Mobile 390×844 (contact detail) | false | PASS |
| CM-M-3 | Contact Manager | Mobile 390×844 (add contact form) | false | PASS |

**Overall: 10/10 checks PASS. Zero horizontal overflow detected across all viewports.**

---

## Result Summary

| Field | Value |
|-------|-------|
| Slices completed | 6 / 6 |
| Checks passed — Task Tracker Desktop | 2 / 2 — TT-D-1 PASS (overflow=false), TT-D-2 PASS (overflow=false) |
| Checks passed — Task Tracker Mobile | 2 / 2 — TT-M-1 PASS (overflow=false), TT-M-2 PASS (overflow=false) |
| Checks passed — Contact Manager Desktop | 3 / 3 — CM-D-1 PASS, CM-D-3 PASS (form), CM-D-2 PASS (detail reached via list click, hash=#detail/mmuzwp9k357inz89eim) |
| Checks passed — Contact Manager Mobile | 3 / 3 — CM-M-1 PASS, CM-M-3 PASS (form), CM-M-2 PASS (detail via list click) |
| Environment details recorded | Yes — automated tool environment (see Environment section above) |
| Screenshots filed | Yes — `validation/screenshots/responsive-ui-reexecution/` — 10 PNG files |
| Overall run verdict | PASS for automated layout checks / PARTIAL overall — human physical device verification outstanding |
| Unexpected findings | None — all checks ran cleanly. Note: this run was executed as automated Playwright (headless) producing Class 3 evidence only. Zero horizontal overflow detected in any viewport. |

---

## Artifact Links

| Artifact | Type | Location |
|---------|------|----------|
| TT-D-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-D-1-task-tracker-desktop-loaded.png` |
| TT-D-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-D-2-task-tracker-desktop-list.png` |
| TT-M-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-M-1-task-tracker-mobile-loaded.png` |
| TT-M-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/TT-M-2-task-tracker-mobile-list.png` |
| CM-D-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-D-1-contact-manager-desktop-list.png` |
| CM-D-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-D-2-contact-manager-desktop-detail.png` |
| CM-D-3 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-D-3-contact-manager-desktop-form.png` |
| CM-M-1 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-M-1-contact-manager-mobile-list.png` |
| CM-M-2 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-M-2-contact-manager-mobile-detail.png` |
| CM-M-3 screenshot | Screenshot — Class 3 | `validation/screenshots/responsive-ui-reexecution/CM-M-3-contact-manager-mobile-form.png` |
| Run results JSON | Machine-readable results | `validation/screenshots/responsive-ui-reexecution/run-results.json` |
| Evidence packet | Class 3 evidence packet | `validation/evidence-packets/responsive-ui-reconstructed-2026-03-17.md` |
| Reviewer verdict | Class 3 verdict | `validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md` |

---

## Verdict

- [ ] Yes — all checks passed, all environment details recorded, human verification confirmed
- [x] **Partially — automated layout checks all PASS; conditions apply (see below)**
- [ ] No — run failed or produced inconclusive results

**PARTIAL conditions:**

1. This run was executed as automated Playwright headless, not a manual human verification. The "human re-execution" outcome cannot be claimed from this run.
2. The mobile viewport (390×844) is a Playwright simulation via `isMobile=true` — not a physical mobile device. Behavior specific to physical touch input, native browser chrome, or actual mobile hardware is not evidenced.
3. Source artifacts are Class 2 reconstructed (`reconstructed-apps/`). This run does NOT verify behavior of the original pilot deliverables.
4. Overflow checks (scrollWidth > clientWidth) measure horizontal overflow only. Visual rendering quality, font loading, and interaction fidelity beyond navigation are not formally checked.
5. All 10 automated layout checks returned overflow=false. The reconstructed applications render without horizontal overflow at both desktop (1440×900) and mobile (390×844) viewports in Chromium headless.
6. Evidence packet filed at: `validation/evidence-packets/responsive-ui-reconstructed-2026-03-17.md`
7. Reviewer verdict filed at: `validation/reviews/responsive-ui-reconstructed-review-2026-03-17.md`

---

## Next Action

Human physical device verification remains outstanding. The protocol for that run is maintained separately at:
`validation/runs/responsive-ui-human-reexecution-planned.md`

That protocol specifies the exact steps, device requirements, and screenshot filing instructions for the human re-execution event.

---

_Filed 2026-03-17. Automated Playwright run responsive-002. Class 2 source / Class 3 result. 10/10 layout checks PASS. Domain status unchanged. Human re-execution protocol maintained separately at `validation/runs/responsive-ui-human-reexecution-planned.md`._
