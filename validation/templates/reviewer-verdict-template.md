# Reviewer Verdict — Template

> **Instructions:** Copy this file to `validation/reviews/{domain}-{project-name}-review-{date}.md`. This document records a formal review of a validation run or evidence packet by a party other than the builder. The builder cannot self-review for Proven status.

---

## Verdict Metadata

| Field | Value |
|-------|-------|
| Reviewer name | |
| Reviewer role | Independent founder / Domain specialist / Framework reviewer |
| Scope reviewed | (validation run / evidence packet / both) |
| Run or packet being reviewed | Link to file |
| Review date | YYYY-MM-DD |
| Verdict | PASS / PARTIAL / FAIL |

---

## 1. Scope Reviewed

What specifically did this review cover?

List each artifact, file, or section examined.

| Item Reviewed | Type | Status |
|---------------|------|--------|
| | Validation run / Evidence packet / Gate result / Artifact | Reviewed / Not reviewed (explain) |

---

## 2. Requirement Review

For each MUST requirement in scope, state whether the evidence supports the claimed truth state.

| Requirement | Claimed State | Evidence Examined | Reviewer Assessment | Notes |
|-------------|---------------|------------------|---------------------|-------|
| | Proven / Tested | | Confirmed / Downgraded / Rejected | |

_If the reviewer downgrades a requirement from Proven to Tested, the domain status cannot be upgraded._

---

## 3. Findings

List any issues, gaps, or concerns found during review.

| Finding | Severity | Required Action |
|---------|---------|-----------------|
| | Blocking / Non-blocking / Advisory | Fix before status update / Document as limit / Accept as-is |

---

## 4. Evidence Quality Assessment

| Factor | Assessment | Notes |
|--------|-----------|-------|
| Completeness — all required artifacts present | Yes / No / Partial | |
| Honesty — claims match evidence, no overclaiming | Yes / No / Concern | |
| Founder verification — independent from builder | Confirmed / Not confirmed | |
| Gate integrity — full gate criteria applied | Confirmed / Abbreviated / Not run | |
| Proof-boundary note present and accurate | Yes / No | |

---

## 5. Verdict

**Overall verdict for this review:**

- [ ] **PASS** — evidence supports the claimed domain status. Status update may proceed.
- [ ] **PARTIAL** — evidence supports a more limited claim. Conditions:
- [ ] **FAIL** — evidence does not support the claimed status. Required corrections:

---

## 6. Required Follow-Up

List any actions required before the domain status can be updated.

| Action | Owner | Deadline |
|--------|-------|---------|
| | | |

---

## 7. Reviewer Sign-Off

**I confirm that this review was conducted independently from the build process, and that the findings above reflect my honest assessment of the evidence on file.**

Reviewer: ___________________
Date: YYYY-MM-DD
Signature / confirmation method: ___________________

---

_This template is part of the CTO Build Framework validation infrastructure. Do not modify the template — copy it for each review._
