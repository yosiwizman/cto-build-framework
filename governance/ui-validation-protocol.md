# UI Validation Protocol

**Type:** Governance artifact

**Purpose:** Establishes the tool-first standard for UI validation across all projects built under the CTO Build Framework. Defines when tool-based verification is required, what proof it must produce, how CI integrates with it, and when human review is permitted as a fallback.

**Date:** 2026-03-18
**Repo:** https://github.com/yosiwizman/cto-build-framework

**Extends:** `governance/llm-operating-discipline.md` — Section 8 (Verification as a Continuous Loop), specifically the Verification Method Hierarchy.

---

## 1. Purpose

This protocol replaces human-first UI validation with tool-first validation for all UI behavior that can be verified by automated means.

**What it establishes:**

- Playwright is the primary and required tool for UI verification on any project built under this framework
- Screenshot capture is mandatory — not optional — for all UI validation runs
- CI-based automated validation is the standard execution path for every pull request that touches UI behavior
- Human review of UI is a defined fallback for cases where tool-based proof is insufficient, not a default practice

**What it does not change:**

- Domain validation statuses in `validation/domain-matrix.md` — this protocol is a governance layer, not new field evidence
- The proof-boundary doctrine — passing tool-based validation does not expand what is "proven" at the domain level
- The existing five Validated domains or their scope boundaries

**Plain-English framing:** If software can be checked by running Playwright, it must be checked by Playwright. Human eyes are reserved for decisions that require judgment that automated tools cannot provide.

---

## 2. Core Principle

> **"If it can be verified by tools, it must be verified by tools first."**

This principle governs all UI validation decisions.

Human review of UI is not the default. It is a fallback — permitted only when:

- The UI behavior requires subjective judgment that cannot be reduced to a pass/fail assertion (for example: does this layout feel right for the intended audience?)
- The UI claim involves a physical device, named OS, or named browser — cases where headless Playwright cannot produce the required evidence
- A Playwright run has failed repeatedly and reached a point where a human needs to determine whether the failure is an environment problem, a test problem, or a genuine product defect

Everything else is tool-first.

**Why this matters:** Human UI review is slow, inconsistent, and hard to reproduce. Tool-based review is fast, repeatable, and produces traceable artifacts. Using human review as the default introduces variability that the governance model is designed to eliminate.

---

## 3. Tooling Standard

### 3.1 Primary tool: Playwright

Playwright is the required browser automation and UI testing tool for all framework-governed projects.

**What Playwright must cover:**

| Capability | Requirement |
|-----------|-------------|
| Page load and render | Every significant page or view must load and render without errors |
| Element presence | Critical UI elements must be present and in the expected location |
| Interaction | Click, input, form submission, navigation — any interaction in the spec must be tested |
| State transitions | If the UI changes state (e.g., list filters, form validation feedback), the before and after states must both be asserted |
| Error states | If an error state is specified in requirements, it must be triggered and verified |

### 3.2 Screenshot capture: mandatory

Every Playwright validation run must produce screenshots. Screenshots are not debugging aids — they are evidence artifacts.

**Screenshot requirements:**

- Captured at key assertion points, not only at failure
- Named clearly (e.g., `contact-list-initial-state.png`, `search-filter-active.png`)
- Stored in the project's `screenshots/` directory
- Retained as part of the evidence record for the slice or feature being verified

A validation run that does not produce screenshots does not produce valid evidence for this framework.

### 3.3 Interaction validation

Playwright must exercise actual user interactions, not just assert static markup. For any feature in the requirements:

- If a user clicks a button, the test must click it and assert the result
- If a user types in a field, the test must type and assert the resulting state
- If navigation occurs, the test must navigate and assert the destination

### 3.4 Visual diff (optional)

Visual diffing tools (pixel-level or layout comparison across runs) may be used to detect regressions between versions. This is not required by this protocol but is permitted as an enhancement when:

- A prior verified screenshot exists as a baseline
- The diff is used to flag regressions, not to establish first-time proof
- The diff result is included in the evidence record

Visual diff results do not substitute for interaction assertions.

---

## 4. Required Proof Output

Every UI validation run must produce the following. A run that does not produce all four is incomplete and does not satisfy this protocol.

| Artifact | What it is | Where it lives |
|----------|-----------|----------------|
| Screenshots | Captured images at key assertion points — both passing states and any failures | `screenshots/` in the project directory |
| Interaction log | Playwright output showing which actions were taken, in what order, and whether each assertion passed or failed | Playwright test output, captured in CI logs |
| Pass/fail status | An explicit pass or fail verdict for each test and for the overall run | CI run result; Playwright exit code |
| CI run reference | A link to or identifier for the specific CI run that produced this result | GitHub Actions run URL or run ID |

These four artifacts together constitute the evidence record for a UI validation run.

---

## 5. CI Integration

### 5.1 GitHub Actions requirement

All framework-governed projects that contain UI must have a GitHub Actions workflow that runs Playwright tests. This is a requirement, not a recommendation.

The workflow must:

- Trigger on every pull request that modifies UI files or UI tests
- Run the full Playwright suite
- Capture screenshots as artifacts
- Report pass/fail status to the PR

**Note:** This protocol defines the requirement. It does not install or configure the workflow. CI implementation is a separate build task, not a governance task. The governance requirement is that it must exist for any project that makes UI-related claims in its evidence record.

### 5.2 PR merge gate

A pull request that touches UI behavior must not be merged without a passing Playwright CI run, if such a workflow is in place for the project.

If no CI workflow exists yet for a project, this requirement applies from the point at which CI is implemented forward. It does not retroactively block existing PRs.

**Plain-English framing:** Once CI is running, "it looks fine to me" is not a merge criterion for UI changes. The CI run result is.

### 5.3 CI is not the only gate

A passing CI run is necessary but not sufficient to satisfy the full release gate. The release gate (as defined in the CTO Build Framework) requires founder verification of all requirements. A CI run is the tool-based component of that verification — not a replacement for it.

---

## 6. Validation Flow

The required validation sequence for any UI feature or change:

```
build
  └── playwright run
        ├── screenshots captured at key assertion points
        ├── interaction assertions executed (click, input, navigate)
        ├── assertions pass/fail evaluated
        └── CI result produced
              ├── PASS → evidence artifacts filed → slice complete
              └── FAIL → see Section 7 (Failure Handling)
```

This flow applies to:
- Every new UI feature being added
- Every UI change being made to an existing feature
- Every release gate verification for a project with UI

The flow must be executed in this order. Screenshots before assertions. Assertions before result. Result before filing evidence.

---

## 7. Failure Handling

When a Playwright run fails, the following sequence applies in order:

### Step 1 — Retry once

Re-run the test suite once in a clean environment. Some failures are transient (timing issues, network conditions, process startup race conditions). A single retry identifies whether the failure is consistent.

### Step 2 — Capture failure screenshots

Whether or not a retry is attempted, failure screenshots must be captured. A failure without a screenshot produces no diagnostic signal and no evidence of what the tool actually encountered.

### Step 3 — Log the error

The Playwright error output, including the specific assertion that failed, the page state at failure, and any console errors, must be logged and retained. "Tests failed" is not a complete failure record. The specific failure with its context is.

### Step 4 — Diagnose before escalating

Before escalating to human review, determine whether the failure is:

| Failure type | Action |
|-------------|--------|
| Environment problem (server not running, port conflict, stale process) | Fix the environment; re-run the test |
| Test configuration problem (wrong selector, incorrect wait, outdated test) | Fix the test; re-run |
| Genuine product defect (the UI behavior does not match the requirement) | Fix the product; re-run |
| Determinism failure (test cannot reach a stable result across multiple runs) | Escalate to human review |

### Step 5 — Escalate to human review only when necessary

Human review of a Playwright failure is permitted only when:

- The tool cannot reach a deterministic result despite environment cleanup and configuration fixes
- The failure involves a judgment call the tool cannot make (e.g., visual layout quality, accessibility, subjective UX)

Human review of a failure that should be diagnosed and fixed is not permitted as a shortcut.

---

## 8. Human UI Gate

Human review of UI is a defined fallback, not a default step.

### When human review IS triggered

| Trigger | Reason |
|---------|--------|
| Tool cannot reach determinism | No automated assertion can reliably pass or fail for the behavior in question |
| Physical device claim required | The evidence must state a named device, OS, or browser — headless Playwright cannot produce this |
| Subjective UX evaluation required | Layout quality, visual polish, or accessibility judgment that cannot be reduced to a pass/fail assertion |
| Complex user journey evaluation | Multi-step flows where the quality judgment depends on context and feel, not just functional correctness |

### When human review is NOT triggered

| Scenario | Correct action |
|---------|----------------|
| "I want to see it before merging" | Run Playwright. If it passes, the CI run is the verification. |
| "The test is flaky" | Fix the test. Do not substitute human review for a broken test. |
| "CI isn't set up yet" | Set up CI. Human review is not a permanent substitute. |
| "It worked on my machine" | That is not evidence. Run the CI suite. |

### What human review produces when triggered

When human review is legitimately triggered, it must produce a documented result:

- What was reviewed
- By whom
- On what device, OS, and browser (for physical-device claims)
- What was verified
- Pass or fail verdict

This record becomes part of the evidence for the slice. An undocumented human UI review produces no evidence that the framework can use.

---

## 9. Proof-Boundary Alignment

This protocol is a governance layer. It is not new field evidence. Using this protocol does not widen the framework's domain validation claims.

**What tool-based UI validation establishes:**

- That a specific UI behavior passed a specific automated test in a specific CI run
- That screenshots exist showing the state of the UI at the time of the run
- That the test run can be referenced, reproduced, and audited

**What tool-based UI validation does NOT establish:**

- That the software is correct in all domains or environments beyond the test
- That a domain moves from Untested to Validated — domain status changes require field evidence, founder verification, and a reviewer verdict, as defined in `validation/domain-matrix.md`
- That Playwright headless verification equals physical-device verification — these are distinct claims with distinct evidence requirements (see `governance/llm-operating-discipline.md` Section 8)
- That any previously Untested domain has been validated by the addition of this protocol

**The scope boundary is unchanged.** The five currently Validated domains remain Validated within their stated scope boundaries. The ten Untested domains remain Untested. The one Partially Validated domain remains Partially Validated. This protocol does not alter any of those states.

**Protocol ≠ proof.** Defining how UI validation should work does not prove that UI validation has been performed. Evidence is produced by running tests, not by defining how to run them.

---

## 10. Integration with LLM Operating Discipline

This protocol extends two specific elements of `governance/llm-operating-discipline.md`:

### Extension of Section 8 — Verification as a Continuous Loop

Section 8 of `llm-operating-discipline.md` defines the Verification Method Hierarchy:

1. Tool-based verification first (Playwright, CI, screenshots)
2. Manual human review for cases tool verification cannot close
3. Playwright headless ≠ physical device

This protocol operationalizes that hierarchy. It moves from principle to procedure: what tools are required, what artifacts they must produce, how CI integrates them, and when human review is permitted. The hierarchy is unchanged — this document defines how to execute it.

### Extension of verification loops

`llm-operating-discipline.md` Section 8 defines verification as a continuous loop: after every slice, after every session, before every handoff. This protocol adds the tool-based execution requirement to that loop for UI work. The loop does not change. The standard for what "verified" means for UI now has a concrete definition: Playwright passed, screenshots exist, CI run is referenced.

### What this protocol does not change in llm-operating-discipline.md

- The eleven operational rules (Section 11) are unchanged
- The scout pass principles (Sections 6, 7) are unchanged
- The micro-slice model (Section 5) is unchanged
- The founder control model (Section 9) is unchanged

---

## Maintenance Note

This protocol is a point-in-time governance artifact as of 2026-03-18. It must be updated if:

- The primary tooling standard changes (e.g., a different automation tool replaces Playwright)
- CI integration requirements change (e.g., a different CI platform is adopted)
- The human review trigger criteria are revised based on field experience
- A field evidence run generates findings that require the protocol to be updated

Updates to this protocol do not automatically change domain validation statuses. A protocol update is a governance change, not an evidence event.

---

_Created: 2026-03-18. One new repo file only. No manuscript edits. No domain status changes. No edits to domain-matrix.md, validation-ledger.md, README.md, or llm-operating-discipline.md._
