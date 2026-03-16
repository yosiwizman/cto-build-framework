# Domain Validation Run — Template

> **Instructions:** Copy this file to `validation/runs/{domain}-{project-name}-{date}.md`. Fill every field. Do not leave fields blank — use "N/A" only where genuinely not applicable, and explain why.

---

## Run Metadata

| Field | Value |
|-------|-------|
| Domain | |
| Project Name | |
| Project Class | Standard / Complex / Domain-Heavy / Specialist |
| Run Date | YYYY-MM-DD |
| Operator | |
| Reviewer (if separate) | |
| Run Status | In Progress / Complete / Abandoned |

---

## 1. Goal

What outcome does this validation run aim to prove?

_One sentence. Be specific. "Prove that the framework's governance loop works for X type of project" is acceptable. "Test stuff" is not._

---

## 2. Hypothesis

What do you expect to find?

_State your prediction before the run. This is not a formality — it forces you to be honest about what you assume before you have evidence._

---

## 3. Scope

**In scope:**
- (list specific features, capabilities, or behaviors being validated)

**Out of scope:**
- (list things explicitly excluded from this run — do not leave this blank)

---

## 4. Environment

| Field | Value |
|-------|-------|
| Tools used | |
| Browser / Runtime | |
| Device(s) | |
| Git branch | |
| Commit at run start | |

---

## 5. Toolchain

List the tools involved in this validation run:
- AI model / version:
- Editor / coding tool:
- Build tool:
- Test method:

---

## 6. Slice Plan

List each planned slice before building begins. Mark status as you go.

| Slice | Description | Status | Notes |
|-------|-------------|--------|-------|
| 1 | | Planned / Built / Verified / Failed | |
| 2 | | | |
| 3 | | | |

_Add rows as needed. Do not skip slices retroactively._

---

## 7. Risks and Unknowns

What could go wrong? What don't you know yet?

_Identify risks before the run, not after. This record matters._

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| | | |

---

## 8. Checkpoints

List each rollback checkpoint saved during the run.

| Checkpoint | Slice | Commit Hash | Description |
|-----------|-------|-------------|-------------|
| | | | |

---

## 9. Test Protocol

How will you verify each requirement?

| Requirement | Test Method | Who Verifies |
|-------------|------------|--------------|
| | | |

_"AI checked it" is not a valid verification method for Proven status. Founder or independent reviewer verification is required._

---

## 10. Result Summary

_Fill this after the run is complete._

| Field | Value |
|-------|-------|
| Slices completed | / total planned |
| Requirements Proven | / total MUST |
| Gate verdict | PASS / FAIL / Not run |
| Unexpected outcomes | |
| Scope drift incidents | None / (describe if any) |

---

## 11. Artifact Links

List every artifact produced by this run.

| Artifact | Type | Location | Version |
|---------|------|----------|---------|
| | Screenshot / Log / Test record / Gate result | | |

---

## 12. Verdict

**Did this run validate the domain?**

- [ ] Yes — all MUST requirements Proven, gate passed, evidence on file
- [ ] Partially — some requirements Proven, conditions apply (describe below)
- [ ] No — run failed or produced inconclusive results (describe below)

**Conditions or limits (if partial):**

---

## 13. Next Action

What happens as a result of this run?

- [ ] Update domain-matrix.md status
- [ ] File evidence packet to `validation/evidence-packets/`
- [ ] Request reviewer verdict
- [ ] Repeat run with corrections
- [ ] Abandon and document why

**Assigned to:**
**Target date:**

---

_This template is part of the CTO Build Framework validation infrastructure. Do not modify the template itself — copy it for each new run._
