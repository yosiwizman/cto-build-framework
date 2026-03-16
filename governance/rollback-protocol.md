# Rollback Protocol

Rollback is the mechanism that makes failure cheap. When a slice fails, the system returns to the last verified checkpoint rather than attempting to patch broken code.

## Checkpoint System

After every successful slice, the system saves a checkpoint — a verified, recoverable state of the software. Checkpoints are the foundation of the rollback system.

A checkpoint captures:
- The complete state of the codebase at that moment
- Which requirements have been verified up to that point
- The evidence captured so far
- The build sequence that produced this state

## When Rollback Occurs

Rollback is triggered when:
- A slice fails and cannot be quickly fixed (Level 1 escalation fails)
- A different approach is needed (Level 2 escalation)
- The founder decides to reject a completed slice
- A scope change invalidates work in progress

## How Rollback Works

1. The failed or rejected slice is discarded entirely
2. The system returns to the last verified checkpoint
3. All evidence captured after that checkpoint is invalidated
4. The build resumes from the clean, verified state

Rollback is mechanical, not aspirational. It loads a saved state. There is no "undo the last three changes and hope it works." The checkpoint is a known-good state, verified by tests and (for completed slices) by the founder.

## Escalation Ladder

When a slice fails, the system follows a structured escalation sequence:

| Level | Response | Decision Maker |
|-------|----------|---------------|
| 1 | Quick fix — minor correction within the same slice | AI (autonomous) |
| 2 | Different approach — rollback and rebuild the slice differently | AI (autonomous) |
| 3 | Stop and ask — present the problem to the founder for guidance | Founder |
| 4 | Pattern detected — multiple slices failing, systemic issue identified | Founder |
| 5 | High-stakes prevention — irreversible action detected, halt before proceeding | Founder |
| 6 | Strategic review — compress, reroute, pivot, or stop the project | Founder |

The escalation ladder ensures that failure is handled proportionally. Small problems get small responses. Systemic problems get strategic responses. The founder is involved only when the decision requires business judgment.

## Failure Containment

The slice-based approach ensures that failure is contained:
- A failed slice affects only that slice — previous verified work is untouched
- Rollback returns to a state where everything verified is still verified
- The next slice starts from a clean, known-good foundation
- Failure cannot cascade backward through previously verified work
