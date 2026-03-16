# Simulation Framework

Simulations are controlled experiments designed to test specific governance mechanisms without requiring a full end-to-end project. They are used to validate that governance components function correctly before they are exercised by real projects.

## Purpose

Simulations fill the gap between "doctrine exists" and "doctrine is proven." A domain overlay for payment processing, for example, can be simulated to verify that the governance rules trigger correctly, evidence requirements are captured, and the release gate incorporates domain-specific checks — all without building a real payment system.

Simulations do not replace field validation. A simulated result moves a domain to **Partially Validated** at most. Full validation requires a real project through the complete governance loop.

## What Simulations Test

### Failure Containment
- Inject a deliberate failure into a slice
- Verify that rollback returns to the last checkpoint cleanly
- Confirm that previous verified work is unaffected
- Confirm that the escalation ladder activates at the correct level

### Rollback Capability
- Save checkpoints at multiple stages of a simulated build
- Trigger rollback from various points
- Verify that each rollback produces the correct known-good state
- Confirm that evidence records accurately reflect the rolled-back state

### System Recovery
- Simulate a session interruption mid-build
- Verify that the handoff document captures the correct state
- Resume the build from the handoff and confirm governance continuity
- Verify that evidence captured before the interruption remains valid

### Governance Loop Validation
- Run a simulated project through all six governance phases
- Verify that each phase produces the correct artifacts
- Confirm that the release gate evaluates all criteria correctly
- Test edge cases: missing evidence, partial verification, scope drift detection

### Domain Overlay Activation
- Simulate a project entering a domain-specific zone (e.g., payment processing)
- Verify that the domain overlay activates and applies the correct constraints
- Confirm that the release gate includes domain-specific evidence requirements
- Test that violations of domain constraints are caught before the gate

## Simulation Protocol

Each simulation follows a standard protocol:

1. **Define the test objective** — What specific governance mechanism is being tested?
2. **Set up the controlled environment** — What project state is needed to begin?
3. **Execute the simulation** — Run the specific scenario
4. **Capture evidence** — Document what happened, what was detected, what was missed
5. **Evaluate against expected behavior** — Did the governance respond correctly?
6. **Document the result** — Record in the appropriate validation document

## Simulation Results

Simulation results are documented in `/validation/partial-domains.md` when they contribute to partial validation of a domain. Full simulation evidence packets follow the format in `/evidence-packets/README.md`.
