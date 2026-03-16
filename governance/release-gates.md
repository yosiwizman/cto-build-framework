# Release Gates

The release gate is the structured evaluation that determines whether software is ready for release. It replaces subjective "it looks done" judgments with a scored, documented verdict.

## Gate Types

### Personal Production Gate
Used when software is built for the founder's own use. Checks that every MUST requirement is founder-verified with evidence, system tests pass, no scope drift occurred, no open blockers remain, evidence is complete and current, and recovery is documented.

Both pilot projects (task tracker and contact manager) used this gate.

### Commercial Release Gate
Used when software will be offered to external users or customers. Includes everything in the personal gate plus: security review, load testing, billing verification, support documentation, monitoring and analytics, and legal compliance.

This gate exists in the framework but has not been field-tested.

## Gate Evaluation Criteria

The gate checks approximately twenty criteria grouped into six categories:

1. **Requirement Verification** — Every MUST requirement must be at Proven or above. Any MUST below Proven is an automatic gate failure.
2. **System Testing** — All automated diagnostics must pass. No critical or high-severity failures may be open.
3. **Scope Drift Check** — What was built must match what was approved. No unauthorized additions, removals, or modifications.
4. **Blocker Check** — No open blockers may exist at gate time. Blockers must be resolved, deferred (with documented rationale), or accepted.
5. **Evidence Completeness** — The evidence record must be complete and current. Evidence must be version-bound to the release candidate.
6. **Recovery Availability** — A rollback path must be documented and functional. If the release fails in production, recovery is possible.

## Scoring

### Confidence Score (out of 35)
Seven factors, each scored 1–5:
- Tests passing cleanly
- Diagnostics healthy
- No critical bugs
- Real data tested
- Recovery tested
- Budget compliance
- Founder satisfaction

Above 28 = high confidence. 21–28 = acceptable. Below 21 = not ready.

### Sufficiency Score (out of 20)
Four factors, each scored 1–5:
- Percentage of requirements with evidence
- Average evidence quality
- Founder personal verification coverage
- No evidence gaps for critical features

Above 16 = sufficient. 12–15 = marginal. Below 12 = evidence too thin.

## Gate Verdict

The gate produces a binary verdict: **PASS** or **FAIL**. A pass requires all MUST requirements at Proven, both scores above threshold, and no open blockers. There is no conditional pass.
