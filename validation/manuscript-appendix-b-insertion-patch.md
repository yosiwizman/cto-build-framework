# Manuscript Appendix B Insertion Patch

**This file is the canonical editor patch for inserting Appendix B and replacing the `[URL]` placeholder in the manuscript.**

An editor applying this patch should follow the instructions below exactly — without improvisation, paraphrase, or scope expansion. Every domain status label, every scope qualifier, and every disclosure note in this patch derives directly from:

- `validation/appendix-b-source.md` — repo-side Appendix B source (primary input for this patch)
- `validation/domain-matrix.md` — canonical domain status source
- `validation/evidence-coverage-matrix.md` Part D — scope boundaries per domain
- `validation/validation-ledger.md` — reviewer verdict states

**Do not:**
- Soften scope qualifiers in the domain table
- Remove the PARTIAL verdict disclosure
- Expand "what's been proven" beyond the five domains listed
- Substitute memory, inference, or a prior draft for the domain table in this file

**Manuscript path:** `C:\Users\yosiw\Downloads\ASSEMBLED_MANUSCRIPT_COMPLETE.md`
**Repo path:** `C:\Users\yosiw\cto-build-framework`
**Repo URL:** https://github.com/yosiwizman/cto-build-framework

**Date created:** 2026-03-17

---

## Patch Scope

This patch does two things and nothing else:

1. **Replace the `[URL]` placeholder** at manuscript line 2324 with the live repo URL.
2. **Insert Appendix B** as a new section at the end of the manuscript, after the final line.

It does NOT:
- Change any domain status label
- Broaden any claim beyond the current evidence boundary
- Edit any existing manuscript chapter
- Remove or soften existing caveats in Ch.6, Ch.11, Ch.13, or Ch.14

---

## Manuscript Anchor Points

| Item | Exact Location | Content |
|------|---------------|---------|
| `[URL]` placeholder | **Line 2324** | Mid-paragraph, inside the sentence: `"...The companion framework (available free at [URL]) includes..."` |
| Appendix B reference | **Line 2324** | Start of same paragraph: `"Appendix B shows the current validation status for every major software domain..."` |
| Last line of manuscript | **Line 2364** | `"That position is yours. You've earned it."` |
| Appendix B insertion point | **After line 2364** | Insert as a new section following the manuscript's final paragraph |

---

## Exact Replacement Instruction — `[URL]` Placeholder

**Location:** Manuscript line 2324

**Find this exact string:**
```
available free at [URL]
```

**Replace with:**
```
available free at https://github.com/yosiwizman/cto-build-framework
```

**Full sentence before replacement:**
> The companion framework (available free at [URL]) includes a complete Domain Validation Matrix with the specific evidence required to validate each domain and example projects designed to test them.

**Full sentence after replacement:**
> The companion framework (available free at https://github.com/yosiwizman/cto-build-framework) includes a complete Domain Validation Matrix with the specific evidence required to validate each domain and example projects designed to test them.

No other text on line 2324 changes.

---

## Exact Appendix B Insertion Text

Insert the following block at the end of the manuscript, after line 2364, as a new top-level section. This text is ready for copy/paste.

---

```
---

# Appendix B — Domain Validation Status

This appendix shows the current validation status for every major software domain the CTO Build Framework is designed to address.

The table below reflects the state of the framework's validation program as of publication. Every status label is bounded by the evidence that supports it — not by the capability the framework was designed to reach. "Validated" means a real project in that domain completed the full governance loop with all required behaviors verified by the founder. "Partially Validated" means the governance mechanisms were designed and partially tested, but no complete project has run through the full loop. "Untested" means the doctrine may exist but no project has been built under governance in that domain.

**Important disclosure:** All five Validated domains have PARTIAL reviewer verdicts. They were validated through the two original pilot projects — a task tracker and a contact manager — which predate the formal independent re-execution requirement now documented in the companion framework. Independent re-execution (a separate, documented run by a party other than the original build operator) has not been completed for any domain. The Validated labels represent the historical pilot result. The proof boundary is real and expanding — it is not yet closed.

## Validation Status by Domain

| Domain | Status | Scope Boundary |
|--------|--------|----------------|
| CRUD / Local-State Applications | **Validated** | Single-page app with localStorage only; no backend, no server persistence |
| Client-Side Multi-Page Apps | **Validated** | Hash routing; client-side state only; no backend, no server |
| Search / Filtering | **Validated** | Name/company search and single category filter proven; Pilot 2 contact manager only; in-memory/localStorage; server-side search, faceted search, and pagination not tested |
| Form Validation | **Validated** | Client-side email format validation only (one field, one rule); no other field types; no required-field enforcement beyond email; no server-side validation tested |
| Responsive UI (Desktop + Mobile) | **Validated** | Founder-verified on desktop and mobile; device names, OS, and browser not recorded; physical device re-execution outstanding |
| Multi-Session Continuity | **Partially Validated** | Handoff protocol designed and documented; both pilots completed in single sessions; no complete multi-session project run on file |
| Authentication / Authorization | **Untested** | Domain overlay designed; no project built under governance |
| Backend / API / Database | **Untested** | Architecture patterns documented; no project built under governance |
| Payments / Compliance (PCI) | **Untested** | PCI overlay designed; no project built under governance |
| Production Deployment / Runtime | **Untested** | Deployment governance designed; no deployment exercised |
| CI / Branch / Merge Governance | **Untested** | Branch governance designed; no project exercised it |
| Swarm / Parallel Execution | **Untested** | Multi-agent orchestration doctrine exists; nothing exercised |
| External Integrations (Third-Party APIs) | **Untested** | No doctrine; no project |
| Real-Time / Event-Driven Systems | **Untested** | No doctrine; no project |
| VoIP / Telephony | **Untested** | No doctrine; no project |
| AI / LLM Workflow Integration | **Untested** | No doctrine; no project |

## How the Proof Boundary Expands

A domain moves from Untested to Validated only when a real project in that domain completes the full governance loop — from scoped requirements through build, founder verification, and a passing release gate — with evidence on file.

The companion framework at https://github.com/yosiwizman/cto-build-framework carries the full Domain Validation Matrix with the specific evidence requirements for each domain, the re-execution requirement for full validation, and the artifact templates needed to document a new domain validation run. Every founder who builds a project under this governance contributes to the evidence base.

## What This Table Does Not Show

This table shows the current state of the validation program, not the full capability of the framework.

- "Untested" does not mean "doesn't work" — it means no project has run the governance in that domain and produced a filed evidence record.
- "Validated" does not mean proven universally — it means the core governance loop was exercised in at least one real project in that domain, within the stated scope boundary.
- The five Validated domains are the honest starting point. The program is designed to expand. The next domains in the validation queue — backend/API development, authentication, and deployment governance — are fully designed and awaiting their first governed pilot projects.

The companion framework is available at https://github.com/yosiwizman/cto-build-framework.
```

---

## Editorial Notes

### Caveats that must remain intact

1. **The PARTIAL verdict disclosure** — the paragraph beginning "Important disclosure: All five Validated domains have PARTIAL reviewer verdicts..." must not be removed or softened. This is the same disclosure that appears in the repo README scope note. It is accurate.

2. **Scope qualifiers on three narrow domains:**
   - **Form Validation** must say "client-side email format validation only (one field, one rule)" — not "form validation" generically. The evidence is R-09 only: one email format check in one form.
   - **Search / Filtering** must say "Pilot 2 contact manager only; in-memory/localStorage; server-side search, faceted search, and pagination not tested" — not "search and filtering" generically.
   - **Responsive UI** must say "Founder-verified on desktop and mobile; device names, OS, and browser not recorded; physical device re-execution outstanding" — not "verified on real devices."

3. **Untested domains with no doctrine** — Real-Time, VoIP, and AI/LLM Workflow Integration appear in the table with "No doctrine; no project." This is accurate. Do not soften to "not yet tested" in a way that implies design work exists.

### Scope qualifiers must not be softened

Every scope boundary in the table was drawn from `validation/domain-matrix.md` and `validation/evidence-coverage-matrix.md` Part D. They exist because the evidence is genuinely narrow. Softening them would create a mismatch between the published appendix and the live repo SSOT — exactly the gap the publication-readiness checklist (items 3.3 and 3.4) was designed to prevent.

### Regeneration requirement before publication

If any domain validation work is completed between now and the publication submission date, this appendix must be regenerated from the live `validation/appendix-b-source.md` before submission. The update sequence is:

1. Complete the validation work and file the artifacts
2. Update `validation/domain-matrix.md`
3. Update `validation/appendix-b-source.md` to match
4. Replace the Appendix B content in the manuscript from the updated `appendix-b-source.md`

Do not update the manuscript Appendix B directly from memory. Always derive it from the repo SSOT.

---

## Safety Check

**This patch is publication-safe if applied exactly as written.**

Conditions that make it safe:

- The `[URL]` replacement uses the live repo URL as documented in `validation/appendix-b-publication-audit.md`.
- The Appendix B domain table matches `validation/appendix-b-source.md` exactly — same 16 rows, same status labels, same scope qualifiers.
- The PARTIAL verdict disclosure is present and unaltered.
- No domain status has been upgraded, broadened, or softened relative to the current repo SSOT.
- The "what this table does not show" section applies the manuscript's own proof-boundary doctrine to the appendix itself — consistent with Ch.6 and Ch.13.

**This patch becomes unsafe if:**

- An editor removes or softens the PARTIAL verdict disclosure before inserting the text.
- The scope qualifiers for Form Validation, Search/Filtering, or Responsive UI are paraphrased or shortened.
- The domain table is edited to add domains not in `validation/domain-matrix.md` or to upgrade status labels without corresponding repo changes.
- The patch is applied to a manuscript version where Appendix B already exists with different content — in that case, the existing content must first be compared against this patch before overwriting.

**Verification step before applying:** Read `validation/appendix-b-source.md` and confirm the domain table in this patch matches it row-for-row. If the repo has been updated since this patch was written, regenerate from the updated source file.

---

## Cross-Reference Files

| File | Role |
|------|------|
| `validation/appendix-b-source.md` | Canonical repo-side source — primary input for this patch |
| `validation/appendix-b-publication-audit.md` | Audit confirming Appendix B was missing; identifies the `[URL]` gap |
| `validation/publication-readiness-checklist.md` | Items 3.3, 3.4 — Appendix B required before publish |
| `validation/domain-matrix.md` | Canonical domain status source |
| `validation/evidence-coverage-matrix.md` | Part D — scope boundaries per domain |
| `validation/manuscript-framework-crosswalk.md` | Editorial safety bridge; Zone 5 = Appendix B drift risk |

---

_Created: 2026-03-17. One new file only. No domain status changes. No manuscript edits. No edits to README, domain-matrix, or validation-ledger._
