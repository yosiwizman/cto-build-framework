# AUTH-1 Independent Operator Handoff Brief

**For:** A separate operator who will independently re-execute AUTH-1
**Read time:** ~5 minutes

---

## 1. What This Is

**AUTH-1** is a validation pilot for the Authentication / Authorization domain of the CTO Build Framework. It is a minimal Node.js + Express application with bcrypt password hashing, express-session management, protected routes, and owner-level authorization.

**Why this re-execution matters:** The original AUTH-1 run was built and tested by the same agent (Claude Code). The founding operator (Yosi Wizman) has personally verified all 10 MUST requirements. The one remaining condition for promoting this domain from **Partially Validated** to **Validated** is independent re-execution by a separate operator — you.

**Current domain status:** Partially Validated. It will not change to Validated until you complete and file this re-execution.

---

## 2. Who You Must Be

To satisfy the independent re-execution requirement, you must be:

- **Not** the original builder (Claude Code / AI agent)
- **Not** the founding operator (Yosi Wizman)
- **Not** anyone who already participated in building, testing, or reviewing AUTH-1

You must be able to run Node.js locally and use a browser. No other technical background is required.

---

## 3. Files You Must Use

| File | Purpose | Path |
|------|---------|------|
| Checklist | Step-by-step execution guide — work through this | `validation/runs/AUTH-1-independent-reexecution-checklist.md` |
| Review template | Verdict form — file this when done | `validation/reviews/AUTH-1-independent-reexecution-template.md` |
| Pilot spec | The original requirements — your ground truth | `validation/pilot-specs/AUTH-1-authentication-authorization.md` |

**Workflow:** Read the checklist. Start the server. Execute each item. Record what you observe. Complete the review template. File it.

---

## 4. What You Must NOT Do

| Do not | Why |
|--------|-----|
| Treat the founder's prior PASS results as your results | Your run is independent — prior results are reference only |
| Skip items because they "obviously work" | Every item must be personally executed or explicitly marked NOT TESTED with a reason |
| Change any domain status files | Only the framework owner updates status after reviewing your filed verdict |
| Hide mismatches | If something behaves differently than expected, record it exactly as observed — mismatches are valuable |
| Widen claims beyond what you personally observe | Record only what you see |

---

## 5. What Counts as a Complete Submission

Your submission is complete when you have filed:

- [ ] The completed checklist (`AUTH-1-independent-reexecution-checklist.md`) — every item marked PASS, FAIL, or NOT TESTED with observed behavior noted
- [ ] The completed review template — renamed to `AUTH-1-independent-reexecution-review-[date]-[your-initials].md` and filed in `validation/reviews/`
- [ ] Discrepancy notes in the review template — even if there are none (write "None")
- [ ] Your operator identity and independence declaration in the sign-off block

Screenshots or a screen recording are not required but strongly strengthen the claim.

---

## 6. Final Reminder

Filing this re-execution does not promote the domain by itself. It provides the evidence. The framework owner will review your filed verdict and, if the results are consistent, will update `validation/domain-matrix.md` and `validation/validation-ledger.md` in a separate commit.

**Authentication / Authorization will remain Partially Validated until that review is complete.**

If you find a mismatch, do not worry — record it accurately. A honest FAIL is more valuable than a silent one.

---

_Created: 2026-03-19. Handoff brief for AUTH-1 independent re-execution. Questions: contact Yosi Wizman (framework owner)._
