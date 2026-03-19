# AUTH-1 Independent Re-Execution Request Packet

**For:** Yosi Wizman (framework owner) to send to an independent operator
**Purpose:** Initiate the AUTH-1 independent re-execution — the final step before the Authentication / Authorization domain can be promoted from Partially Validated to Validated

---

## What You Are Asking the Operator to Do

Run a short local verification of a Node.js authentication application. The operator will test 10 specific behaviors (registration, login, session persistence, logout, access control) in a browser, record what they observe, and file a completed result form.

Total time estimate: 30–60 minutes including setup.

No coding required. The application is already built.

---

## Files the Operator Must Read and Use

All files are in the repo: `https://github.com/yosiwizman/cto-build-framework`

| File | What it is |
|------|-----------|
| `validation/runs/AUTH-1-independent-operator-handoff.md` | Start here — brief overview of what this is and why it matters |
| `validation/runs/AUTH-1-independent-reexecution-checklist.md` | The execution checklist — work through this item by item |
| `validation/reviews/AUTH-1-independent-reexecution-template.md` | The result form — complete and file this when done |
| `validation/pilot-specs/AUTH-1-authentication-authorization.md` | The original requirements — reference if anything is unclear |

---

## Environment the Operator Needs

- Node.js installed (v18 or later)
- A modern browser (Chrome recommended)
- The application source: `~/auth-pilot/` directory on the local machine where the run was originally built (Yosi's machine), **or** a fresh setup from the source files if the operator is on a different machine

> **Note for founder:** If the operator is running on a different machine, the `~/auth-pilot/` directory needs to be transferred or the application needs to be set up fresh. The `auth-pilot` directory is outside the repo. You will need to share: `server.js`, `package.json`, and `package-lock.json`. The operator runs `npm install` then `node server.js`.

---

## What the Operator Must Submit Back

1. **Completed checklist** — every item marked PASS, FAIL, or NOT TESTED with observed behavior noted
2. **Completed review template** — saved as `AUTH-1-independent-reexecution-review-[date]-[their-initials].md` and filed in `validation/reviews/`
3. **Discrepancy notes** — if any behavior differed from expected, it must be described (if nothing differed, they write "None")
4. **Operator identity and independence declaration** — signed off in the review template

---

## Independence Requirements (Plain English)

The operator must:
- Have had **no involvement** in building the auth-pilot application
- Have had **no involvement** in writing or running the original Puppeteer tests
- Be a **separate person** from Yosi Wizman

The operator does not need to be a developer. They need to be able to run a Node.js server and use a browser.

---

## What Counts as a Mismatch That Must Be Reported

The operator should report any of the following:
- A step that is supposed to return PASS but returns an error or unexpected result
- A login that succeeds when it should be rejected
- A session that does not persist when it should, or persists when it should not
- A protected route that is accessible without authentication
- An authorization check that does not enforce the 403 correctly (via the API — see AUTH-1.09 note below)
- A tampered session that is accepted instead of rejected

**AUTH-1.09 known UI note:** The UI may show notes from other users. This is a known display issue — not a security failure. The operator verifies the API behavior (403 returned), not the UI display. The checklist explains this clearly.

A mismatch is not a problem — it is information. The operator should record it honestly.

---

## Copy/Paste Request Message

> **Subject: AUTH-1 Independent Verification Request**
>
> Hi [name],
>
> I'm asking for your help with a short technical verification step for a project I'm working on. It involves running a simple Node.js application locally and testing 10 behaviors in a browser.
>
> Estimated time: 30–60 minutes.
>
> No coding required — the application is already built. You just need Node.js installed and a browser.
>
> Here's what I need:
>
> 1. Read this first (2 min): `validation/runs/AUTH-1-independent-operator-handoff.md`
> 2. Start the server and work through the checklist: `validation/runs/AUTH-1-independent-reexecution-checklist.md`
> 3. Complete and file the result form: `validation/reviews/AUTH-1-independent-reexecution-template.md`
>    — save your completed version as: `AUTH-1-independent-reexecution-review-[today's date]-[your initials].md`
>    — file it in the `validation/reviews/` folder of the repo
>
> All files are in: https://github.com/yosiwizman/cto-build-framework
>
> Important: you need to be someone who was not involved in building or testing this application originally. I'll explain more if you have questions.
>
> Please record exactly what you observe — if something behaves differently than expected, that's useful information, not a problem.
>
> Thank you.

---

## Reminder

**Authentication / Authorization remains Partially Validated** until:
1. An independent operator files a completed re-execution checklist and review template
2. The filed evidence is reviewed by the framework owner
3. The domain-matrix.md and validation-ledger.md are updated in a separate commit

Filing the re-execution evidence does not automatically promote the domain. It provides the evidence for the promotion review.

---

_Created: 2026-03-19. Founder-facing request packet for AUTH-1 independent re-execution. Authentication/Authorization domain: Partially Validated. One condition remaining: independent re-execution by separate operator._
