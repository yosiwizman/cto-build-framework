# AUTH-1 Independent Re-execution — Acceptance & Promotion Criteria

**Purpose:** This file defines the exact conditions under which an independent operator submission for AUTH-1 may be accepted as valid evidence, rejected as incomplete or invalid, and used to trigger a domain status promotion review. It is an enforcement artifact — not a guideline.

**Governed by:** `validation/pilot-specs/AUTH-1-authentication-authorization.md`, `validation/reviews/AUTH-1-independent-reexecution-template.md`, `validation/runs/AUTH-1-independent-reexecution-checklist.md`, and `CLAUDE.md` proof-boundary doctrine.

---

## Section A — Acceptance Checklist

All conditions below must be satisfied before the submission is treated as valid independent re-execution evidence. Any unsatisfied condition means the submission does not satisfy the requirement.

| # | Condition | Required State |
|---|-----------|---------------|
| A1 | Review template filed at `validation/reviews/AUTH-1-independent-reexecution-review-[date]-[initials].md` | Present and committed to repo — not the blank template |
| A2 | Operator name filled | Non-blank |
| A3 | Operator role and relationship to project filled | Non-blank |
| A4 | Independent from original builder (Claude Code) | **Yes** |
| A5 | Independent from founding operator (Yosi Wizman) | **Yes** |
| A6 | Prior involvement in AUTH-1 build or testing | **No** |
| A7 | Environment fields complete | Device, OS, browser, Node.js version, server port 3847 — all filled |
| A8 | All 10 per-requirement rows have a result | PASS, FAIL, or NOT TESTED — no blank rows |
| A9 | "Matches Original" column completed | Y or N for each of the 10 rows |
| A10 | Discrepancy section completed | "None" or specific entries — not left blank |
| A11 | Final verdict selected | Exactly one of: Matches Original / Partial Mismatch / Material Mismatch |
| A12 | Promotion recommendation selected | Exactly one of the three options |
| A13 | Reviewer limitation declaration completed | All sub-fields answered |
| A14 | Operator sign-off checked and dated | Checkbox marked and date present |

**Minimum threshold:** All 14 conditions must be met. There is no partial acceptance.

---

## Section B — Rejection Checklist

The submission is rejected and does not satisfy the independent re-execution requirement if **any** of the following are true.

| # | Condition | Rejection Trigger |
|---|-----------|------------------|
| B1 | A4 is No | Operator is not independent from builder — requirement not satisfied |
| B2 | A5 is No | Operator is not independent from founding operator — requirement not satisfied |
| B3 | A6 is Yes | Operator had prior involvement — requirement not satisfied |
| B4 | Operator name is blank | Anonymous submission cannot establish independence |
| B5 | Fewer than 8 of 10 requirement rows have a result | Substantial incompleteness; NOT TESTED is acceptable only with a per-item reason given |
| B6 | No observed behavior described anywhere | Bare PASS/FAIL with zero notes anywhere in the document — operator may not have actually executed the steps |
| B7 | Discrepancy section blank | Not "None" — just empty; operator did not confirm whether mismatches exist |
| B8 | No final verdict selected | Template returned without a verdict |
| B9 | Filed file is the unmodified blank template | All fields still contain placeholder text |
| B10 | Server port differs from 3847 without documented reason | Execution environment materially different from original run |
| B11 | Database described as persistent (not in-memory SQLite) without explanation | Execution environment materially different from original run |

**If any B-condition is triggered:** Stop. Do not proceed to Section C. Return the submission to the operator with the specific B-condition(s) that failed.

---

## Section C — Promotion-Readiness Checklist

All conditions below must be true before any change is made to `validation/domain-matrix.md` or `validation-ledger.md`. This checklist is entered only after the submission has passed Section A in full with zero Section B rejections.

| # | Condition | Required State |
|---|-----------|---------------|
| C1 | Section A: all 14 conditions satisfied | Yes — confirmed |
| C2 | Section B: zero rejection conditions triggered | Yes — confirmed |
| C3 | Final verdict | **Matches Original** only — Partial Mismatch or Material Mismatch blocks promotion |
| C4 | Promotion recommendation | **Supports promotion review** — any other selection blocks promotion |
| C5 | Discrepancy section | "None" or contains only non-blocking items that do not contradict original proof claims |
| C6 | AUTH-1.09 result | PASS (API 403 confirmed) — known UI display issue noted but not treated as FAIL |
| C7 | Filed review template committed to `validation/reviews/` and present on master | Yes — SSOT update commit must come after, not before or in the same commit as the review file |
| C8 | `domain-matrix.md` and `validation-ledger.md` updated in the same commit | Never one without the other |
| C9 | Commit message names the domain, the independent operator, and the artifact being added | Yes |
| C10 | No other domains or unrelated files changed in the SSOT update commit | Yes — scope is Authentication / Authorization only |

**If any C-condition is not met:** Do not update SSOT. Document which condition blocked promotion and what is required to resolve it.

---

## Section D — Verdict Rule

**Authentication / Authorization must remain Partially Validated** unless and until all three of the following are simultaneously true:

1. **An independent operator submission passes Section A in full** — all 14 acceptance conditions met, zero Section B rejections
2. **The submission carries a Matches Original verdict and a Supports promotion review recommendation** — both required; neither alone is sufficient
3. **The SSOT is updated in a deliberate, artifact-backed commit** — `domain-matrix.md` and `validation-ledger.md` updated together, in a commit that names the operator and the filed review artifact, made only after the review file is already on master

No submission, no match, no update. No status change may be made by assertion, implication, or inference. The evidence must exist, be valid, and be deliberately reviewed before any promotion commit is made.

**This rule supersedes any summary, note, or inference elsewhere in the repo.** If a status update is proposed without a filed, accepted, Matches Original independent re-execution verdict on master, it must be rejected.

---

_Created: 2026-03-20. Enforcement artifact. Governs acceptance, rejection, and promotion-readiness decisions for AUTH-1 independent re-execution submissions. Authentication / Authorization: Partially Validated. No status change without evidence._
