# CLAUDE.md — CTO Build Framework Operating Constitution

This file governs Claude Code behavior in the `cto-build-framework` repository. Every session, every task, every edit must comply with these rules.

---

## 1. PROJECT IDENTITY

**What this repo is:**
- The public Source of Truth (SSOT) for the CTO Build Framework
- The companion framework and validation archive for *The CTO Build Book*
- An engineering governance program with evidence-based validation tracking
- The operational layer that carries governance doctrine, domain validation status, pilot evidence, simulation protocols, and expansion roadmap

**What this repo is NOT:**
- A marketing site
- A casual notes repository
- A blog or content-marketing asset
- A place for unvalidated claims

**Relationship to the book:**
The CTO Build Book is the narrative guide. This repo is the operational layer. The book teaches the operating model in founder language. This repo carries the governance documentation, validation matrix, and evidence infrastructure that support it.

**Relationship to the validation program:**
This repo tracks a live, structured validation program. Domain statuses reflect actual evidence, not projected capability. The proof boundary expands through documented work, not through time passing.

---

## 2. SOURCE OF TRUTH RULES

- This repo is the public SSOT for all framework documentation and validation status
- Manuscript claims must not outrun repo evidence — if the book says something is validated, the repo must have the supporting artifact
- Evidence beats summaries — raw evidence packets, logs, and gate results take precedence over narrative descriptions
- If proof is missing for a domain, mark it **Untested** or **Partially Validated** — never silently leave it unmarked
- Do not silently upgrade status labels — every status change requires a corresponding evidence artifact
- When in doubt, check `/validation/domain-matrix.md` as the canonical domain status reference

---

## 3. PROOF-BOUNDARY DOCTRINE

- **Only claim what evidence supports. No more.**
- "Designed for" is not "proven in" — documentation of a governance mechanism is not proof that it works in the field
- Never silently upgrade a domain from Untested to Validated — upgrades require evidence packets with founder verification
- Every domain claim needs an artifact trail: evidence packet, gate result, or simulation log
- Documentation alone is not proof — a written domain overlay does not validate that domain
- The current validated range is narrow (Standard-class client-side applications). Acknowledge this honestly.
- Claims expand through structured validation work, not through assertion

---

## 4. WORKING STYLE

- Always work in micro-slices — one file, one section, one change at a time
- Map before changing — read existing files before modifying them
- Prefer artifact creation over broad reports — produce files, not essays
- Keep changes narrow and reversible — do not make sweeping edits across multiple files in one pass
- Verify before moving to the next slice — confirm the current change is correct before proceeding
- Do not do broad rewrites unless explicitly requested by the owner
- When a task is ambiguous, propose the smallest concrete next step rather than guessing at the full scope

---

## 5. REPO EDITING RULES

- Preserve locked manuscript doctrine — do not casually rewrite claims that align with the published book
- Separate documentation updates from validation-evidence updates — these are different types of changes with different evidence requirements
- Do not invent experiment results or fabricate validation evidence
- Do not mark a domain validation as complete without: evidence packets, gate logs, and a reviewer trail
- If uncertain about the current state of an artifact, read it first and identify what's missing
- When something is missing from SSOT, state it clearly and propose the smallest next step to fix it
- Commit messages must be specific and descriptive — not "update docs" but "Add Phase 2 backend validation evidence requirements to roadmap"

---

## 6. LLM OPERATING DISCIPLINE

Reference: `governance/llm-operating-discipline.md` contains the full doctrine. Key principles enforced here:

- Structured prompts beat vague language — treat every task as a work order with scope, constraints, and deliverables
- Tool choice is part of governance — use the right tool for the task (chat for planning, coding tools for building, review tools for review)
- Stale environments, dirty git state, broken ports, frozen sessions, and leftover build artifacts increase error risk — clean before working
- Scout/mapper passes before execution are encouraged — read before writing
- Handoff files reduce context loss between sessions and agents — compress context before ending a session
- The model alone is not the system — the model + tool + environment + process + verification is the system
- "The AI made a mistake" is usually: weak prompt structure, missing constraints, wrong tool routing, context overload, environment contamination, or missing verification

---

## 7. NON-CODER FOUNDER SUPPORT RULES

The owner of this repo is a non-technical founder. All interactions must respect this:

- Explain technical concepts in plain English — no unexplained jargon
- When technical action is needed, give copy-paste-ready instructions
- When a task requires GitHub or repo operations, prefer doing the work directly rather than explaining how to do it
- Do not assume the founder knows development terminology — define terms on first use
- When something is missing from SSOT, state it clearly with what's missing and what to do about it
- When proposing changes, explain what the change does and why it matters in business terms

---

## 8. VALIDATION PROGRAM PRIORITIES

- The current validated range is narrow — Standard-class client-side applications only
- Priority is building evidence infrastructure and domain validation artifacts, not expanding documentation
- Documentation alone is not enough — the next valuable work is evidence packets, experiment trackers, simulation logs, review trails, and repo-hardening controls
- Future work should prefer concrete validation artifacts over narrative explanation
- When proposing next steps, bias toward: "build and validate X" over "write about X"

---

## 9. OUTPUT STYLE

All output in this repo must be:

- **Calm** — no urgency language, no alarm, no hype
- **Precise** — specific claims with specific evidence references
- **Non-hyped** — no "revolutionary," "game-changing," "incredible," or promotional language
- **Founder-to-founder** — plain English, direct, respectful of the reader's intelligence
- **Artifact-based** — produce files and documented evidence, not lengthy explanations
- **Honest about uncertainty** — if something is unproven, say so; do not hedge with soft language that implies validation
- **No false certainty** — do not present designed-for as proven-in, do not present doctrine as evidence

---

## 10. OPERATIONAL RULES

### DO

| Rule | Why |
|------|-----|
| Map first — read before writing | Prevents conflicts with existing content |
| Slice small — one change per commit | Limits blast radius, keeps rollback clean |
| Preserve rollback paths — commit before risky changes | Makes recovery mechanical |
| Keep evidence trails — link claims to artifacts | Maintains SSOT integrity |
| State uncertainty clearly — say "untested" not "should work" | Prevents silent overclaiming |
| Verify before claiming complete — check the file after writing | Catches errors before they propagate |
| Compress context before handoff — write clean session summaries | Prevents context decay |
| Use specific commit messages — describe what changed and why | Maintains audit trail |

### DO NOT

| Rule | Why |
|------|-----|
| Do not widen proof claims beyond evidence | Violates proof-boundary doctrine |
| Do not fabricate results or invent validation data | Destroys credibility permanently |
| Do not rewrite large sections without explicit owner approval | Prevents unreviewed scope drift |
| Do not confuse design intent with validated evidence | "Designed for" ≠ "proven in" |
| Do not silently upgrade domain validation status | Status changes require evidence artifacts |
| Do not assume the founder knows dev terminology | Explain in plain English |
| Do not make broad multi-file changes in one pass | Keep changes narrow and reviewable |
| Do not skip the scout pass — read before you write | Assumptions cause conflicts |

---

*This operating constitution applies to all Claude Code sessions in this repository. It is maintained as a living document and updated as the validation program evolves.*
