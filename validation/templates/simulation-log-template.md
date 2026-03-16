# Simulation / Rollback / Recovery Log — Template

> **Instructions:** Copy this file to `validation/simulations/{scenario-name}-{date}.md`. Fill every field. Simulation logs document controlled failure tests, rollback drills, and recovery exercises. They are part of the proof record.

---

## Log Metadata

| Field | Value |
|-------|-------|
| Scenario name | |
| Date | YYYY-MM-DD |
| Operator | |
| Project / Domain context | |
| Log status | Planned / In Progress / Complete |

---

## 1. Scenario Description

What situation does this simulation test?

_Examples: "Simulate a mid-build slice failure and recover from checkpoint." "Test rollback after a failed architecture decision." "Simulate context overload mid-session and restart with handoff document."_

---

## 2. Trigger

What condition initiates this scenario?

_Describe the specific event or state that kicks off the simulation._

---

## 3. Pre-Simulation State

| Field | Value |
|-------|-------|
| Checkpoint available | Yes / No |
| Checkpoint commit hash | |
| Git status at start | Clean / Dirty (describe) |
| Known risks entering simulation | |

---

## 4. Expected Behavior

What should happen when this scenario plays out correctly?

_State the expected outcome before you run the simulation. This is the pass condition._

---

## 5. Observed Behavior

What actually happened?

_Fill this during or immediately after the simulation. Be precise. "It worked" is not sufficient._

---

## 6. Rollback Point

| Field | Value |
|-------|-------|
| Rollback was needed | Yes / No |
| Rollback target | Checkpoint / Commit hash / Manual reconstruction |
| Rollback method | git reset / branch switch / file restore / other |
| Rollback success | Yes / Partial / No |
| Time to recover | |

---

## 7. Recovery Result

**Did the system return to a verified working state?**

- [ ] Yes — verified working after recovery
- [ ] Partial — partially recovered (describe what remains broken):
- [ ] No — recovery failed (describe what happened):

---

## 8. Lessons

What does this simulation teach?

| Lesson | Applies to | Action Required |
|--------|-----------|-----------------|
| | This project / All projects / This domain | Fix / Document / Accept |

---

## 9. Artifact Links

| Artifact | Type | Location |
|---------|------|----------|
| | Screenshot / Log / Commit / Handoff doc | |

---

## 10. Simulation Verdict

- [ ] Pass — scenario played out as expected, recovery successful
- [ ] Partial — scenario partially confirmed, conditions apply (describe):
- [ ] Fail — scenario exposed a gap in the recovery path (describe):

**Follow-up required:**

---

_This template is part of the CTO Build Framework validation infrastructure. Do not modify the template — copy it for each simulation run._
