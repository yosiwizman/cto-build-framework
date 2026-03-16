# Audit Separation

A fundamental principle of the CTO Build Framework: the system that builds the software cannot be the sole auditor of the software it built.

## The Problem

AI-assisted development creates a structural conflict of interest. The AI writes the code, tests the code, and reports on whether the code works. When the same system is both builder and auditor, errors are systematically invisible — the system's blind spots in building are the same blind spots in testing.

This is the "student grading their own exam" problem. The student might be right — might even be right most of the time. But the grade doesn't become trustworthy until someone independent looks at the answers.

## How the Framework Addresses This

### Layer 1: AI Self-Testing (Tested State)
The AI runs its own checks during the build. Tests pass, diagnostics are clean, the system believes the feature works. This is valuable as a first filter — it catches obvious errors before they reach the founder. But it is necessary, not sufficient.

### Layer 2: Founder Verification (Proven State)
The founder personally tests the software. Clicks buttons, enters data, checks behavior, confirms results match expectations. This is independent verification by someone who did not write the code. Evidence is captured (screenshots, test records) and tied to the specific version being tested.

### Layer 3: Evidence Record (Documentation)
Every verification is documented with what was checked, by whom, against which version, and what evidence was captured. The evidence record exists independently of anyone's memory or confidence.

### Layer 4: Release Gate (Structured Evaluation)
The gate is a structured checklist, not a subjective judgment. It checks evidence, not feelings. It produces scores, not opinions. It can be re-run, audited, and challenged.

## Why This Matters

Without audit separation:
- The AI says "all tests passing" and the founder interprets this as "it works"
- Bugs in the AI's logic produce bugs in the AI's tests, which both pass
- Nobody independently verifies that the software does what was asked
- Claims about software quality are based on the builder's assurance, not independent evidence

With audit separation:
- The AI's self-assessment is one input, not the final word
- The founder's independent verification is required for every MUST requirement
- Evidence exists regardless of anyone's confidence
- Claims are bounded by documented, verifiable proof
