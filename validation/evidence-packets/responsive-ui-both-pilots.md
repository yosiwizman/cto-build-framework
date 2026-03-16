# Evidence Packet — Responsive UI (Desktop + Mobile) — Both Pilots

> **Packet type:** Formalization of pre-template evidence. Responsive UI is a cross-cutting domain proven across two pilots rather than a primary domain of a single project. The underlying pilots and gate events occurred before this evidence infrastructure existed. This packet records what the repo can currently support. Fields marked "Not on file" reflect honest gaps.

---

## Packet Metadata

| Field | Value |
|-------|-------|
| Claim being proven | The CTO Build Framework governance loop works for Standard-class, client-side web applications that require responsive layouts verified on desktop and mobile devices |
| Domain | Responsive UI (Desktop + Mobile) |
| Project | Class 1 Pilot (Task Tracker) + Class 2 Pilot (Contact Manager) — both contribute |
| Software version at time of evidence capture | Not on file — no commit hash or version tag captured at gate time for either pilot |
| Date evidence captured | Not on file — both pilots pre-date the evidence template system |
| Evidence captured by | Founding operator (name not formally recorded in repo) |
| Packet prepared by | CTO Build Framework repository — formalization pass, 2026-03-16 |
| Packet version | 1.0 — initial formalization |

---

## 1. The Claim

In both the Task Tracker (Class 1) and Contact Manager (Class 2) pilots, responsive layout — verified on desktop and mobile devices — was a named MUST requirement that reached Proven status and was included in passing release gates.

The CTO Build Framework governance loop produces applications that lay out correctly on desktop and mobile, as verified by the founding operator, within the scope of Standard-class, client-side web applications.

This claim is supported by two independent pilot completions, both of which included responsive layout as a required and verified feature.

---

## 2. What This Claim Does NOT Cover

- Specific device families, screen sizes, or resolutions — no device inventory was formally recorded
- Specific breakpoints — the pixel widths at which layout changes were not formally documented in either pilot
- Tablet-specific layouts — "desktop and mobile" is stated; tablet behavior is not separately evidenced
- Browser compatibility across multiple browsers — no browser matrix was recorded
- Accessibility compliance (WCAG or similar) — not a named requirement in either pilot
- CSS framework or methodology validation — the responsive approach used is not formally specified in existing pilot records
- Any responsive behavior beyond what was manually observed by the founding operator in these two pilots
- Server-rendered or native mobile applications — both pilots were client-side web applications

---

## 3. Artifact List

| # | Artifact | Type | Description | File / Location |
|---|---------|------|-------------|-----------------|
| 1 | Task Tracker pilot documentation | Project record | R-08 (Responsive layout, desktop + mobile) listed as Proven; architecture confirms responsive design | `pilots/task-tracker.md` |
| 2 | Contact Manager pilot documentation | Project record | R-11 (Responsive layout, desktop + mobile) listed as Proven; architecture confirms responsive design | `pilots/contact-manager.md` |
| 3 | Validated domains record — Responsive UI entry | Domain evidence summary | States "Both applications verified by founder on desktop and mobile devices, layout adapts correctly to screen sizes" | `validation/validated-domains.md` |
| 4 | Domain matrix entry | Status record | Responsive UI listed as Validated, evidenced by both pilots | `validation/domain-matrix.md` |
| 5 | Task Tracker screenshots and test records | Founder verification evidence | Described as "founder-verified with screenshots and test records on file" in `pilots/task-tracker.md` | **Not filed in this repository** — referenced as existing externally |
| 6 | Contact Manager screenshots and test records | Founder verification evidence | Described as "founder-verified with screenshots and test records on file" in `pilots/contact-manager.md` | **Not filed in this repository** — referenced as existing externally |

**Artifact gap noted:** Items 5 and 6 are referenced in the pilot documentation but the underlying files (screenshots, test records) are not present in this repository. This packet is incomplete until those artifacts are filed here.

---

## 4. Requirement Evidence

Responsive UI was a named MUST requirement in both pilots.

| Requirement | Pilot | Truth State | Evidence Artifact | Verified By | Notes |
|-------------|-------|-------------|------------------|-------------|-------|
| R-08: Responsive layout (desktop + mobile) | Task Tracker (Class 1) | Proven | `pilots/task-tracker.md` (stated as Proven) | Founding operator | Device(s) verified on not formally recorded; screenshots referenced but not filed in repo |
| R-11: Responsive layout (desktop + mobile) | Contact Manager (Class 2) | Proven | `pilots/contact-manager.md` (stated as Proven) | Founding operator | Device(s) verified on not formally recorded; screenshots referenced but not filed in repo |

**Note on Proven status:** Both pilot records assert Proven status with founder verification referenced. Physical verification artifacts (screenshots) are described as existing but are not filed in this repository. Proven status rests on the pilot records' assertions plus the passing gate verdicts in each pilot. No specific devices, browsers, or breakpoints are documented in any existing repo file.

---

## 5. Founder Verification

**Did the founding operator independently verify the software?**

- [x] Yes — verified on the following device(s): **Not formally recorded.** The `validation/validated-domains.md` record states "Both applications verified by founder on desktop and mobile devices." Neither pilot document specifies which devices were used.

**Founder verification notes:**

Founder verification is asserted in both pilot records and in the validated-domains summary. The domain matrix records evidence from both pilots. The specific devices (make, model, OS version), browsers, and viewport sizes used during verification are not documented in any existing repo file. This is the single most significant gap in this packet — responsive behavior is inherently device-dependent, and the absence of device details weakens the audit trail for this specific domain compared to logic-based features where device variance is lower.

---

## 6. Reviewer Verification

**Was this packet reviewed by a party other than the builder?**

- [ ] No — neither pilot was conducted with a reviewer verdict process in place. No independent reviewer has formally signed off on this evidence packet.

**Impact:** Known gap. A reviewer verdict should be filed at `validation/reviews/` to complete this evidence chain. For responsive UI specifically, reviewer verification would ideally include independent device testing beyond the founding operator's own verification.

---

## 7. Release Gate Results

**Task Tracker (Class 1 Pilot):**

| Field | Value |
|-------|-------|
| Gate type used | Personal Production Gate |
| Confidence score | 28 / 35 |
| Sufficiency score | 16 / 20 |
| Gate verdict | PASS |
| Gate record location | Recorded in `pilots/task-tracker.md` — no separate gate record file exists |

**Contact Manager (Class 2 Pilot):**

| Field | Value |
|-------|-------|
| Gate type used | Personal Production Gate |
| Confidence score | 27 / 35 |
| Sufficiency score | 15 / 20 |
| Gate verdict | PASS |
| Gate record location | Recorded in `pilots/contact-manager.md` — no separate gate record file exists |

**Note:** Responsive layout was one MUST requirement among many in each gate. It contributed to — but was not separately gated from — the full requirement set in each pilot.

---

## 8. Proof-Boundary Note

**What does this evidence prove?**

Standard-class, client-side web applications built under the CTO Build Framework governance loop can produce layouts that the founding operator judges to be correct on both desktop and mobile devices. This has been verified twice — across two different application types (single-page CRUD and multi-page application with routing) — which provides two independent data points rather than one. Responsive layout is a consistent MUST requirement in both pilots, not an afterthought.

**What does this evidence NOT prove?**

- That specific breakpoints were tested or perform correctly at precise pixel widths
- That any particular device family, screen resolution, or OS version was tested
- That cross-browser rendering was verified
- That tablet layouts specifically were tested
- That the responsive behavior meets any formal accessibility or design standard
- That a third party independently verified the responsive behavior
- That this works outside the narrow scope of Standard-class, client-side, React-based applications

Do not cite this packet as evidence for responsive behavior in server-rendered applications, native mobile applications, or any scope beyond Standard-class client-side web apps. Do not cite it as evidence that specific breakpoints or device families were tested.

---

## 9. Unresolved Limits

| Limit | Impact | Status |
|-------|--------|--------|
| Screenshots not filed in repo | Evidence for R-08 and R-11 exists by assertion, not by file | Accepted — acknowledged gap; file if available |
| Device names, OS versions not recorded | Audit trail for responsive verification is incomplete; cannot confirm which devices were tested | Needs follow-up — this is the most significant gap for a layout-dependent claim |
| Browser and browser versions not recorded | Cannot confirm which rendering engines were tested | Accepted — low risk for simple layouts; noted as known limit |
| Specific breakpoints not formally documented | "Desktop + mobile" is a subjective judgment, not a tested technical boundary | Accepted — claim remains narrow ("founder judged layout correct") rather than asserting pixel-perfect breakpoint behavior |
| No independent reviewer verdict | Packet lacks formal third-party review | Needs follow-up |
| Responsive requirement was part of a full pilot gate, not separately gated | Responsive behavior passed as part of the whole, not in isolation | Accepted — correct approach for Standard-class pilot gate |
| No rollback/simulation drill related to responsive layout | Not applicable to this domain type | Accepted — rollback drills are primarily relevant to build-process failures, not UI layout verification |

---

## 10. Packet Status

- [ ] Complete — all sections filled, artifacts on file, ready for ledger update
- [x] **Incomplete** — missing:
  - Physical screenshots for R-08 (Task Tracker) and R-11 (Contact Manager) not filed in this repository
  - Device names, OS versions, and browser details not recorded for either pilot
  - Specific breakpoints tested not documented
  - No independent reviewer verdict on file

**Filed as honest formalization of the available repo truth.** Advances the evidence chain from "none on file" to "filed with known limits." The device-detail gap is the most material weakness in this packet relative to others — responsive behavior is inherently device-dependent, and the missing device record is more consequential here than for logic-based features.

---

_Formalized 2026-03-16. Source truth: `pilots/task-tracker.md`, `pilots/contact-manager.md`, `validation/validated-domains.md`, `validation/domain-matrix.md`. No new evidence was created — existing repo truth was structured into canonical format._
