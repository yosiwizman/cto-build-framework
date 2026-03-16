# Evidence Packets

This directory contains evidence packets from validated projects. Each packet documents a project that passed through the full CTO Build Framework governance loop.

## What Is an Evidence Packet?

An evidence packet is a structured record of a project's validation. It provides the documentation needed to expand the proof boundary into a new domain.

## Packet Format

Each evidence packet must include:

### 1. Project Summary
- Project name and description
- Domain(s) covered
- Project class (Standard / Complex / Domain-Heavy / Specialist)
- Date of release gate

### 2. Requirements Table
- Full list of MUST and NICE requirements
- Final truth state for each requirement
- Evidence source for each Proven requirement

### 3. Architecture Summary
- Architecture type and key decisions
- Technology choices with rationale
- What was deliberately avoided and why

### 4. Build Summary
- Number of slices
- Number of checkpoints saved
- Escalation events (if any)
- Scope drift incidents (if any — should be zero)

### 5. Release Gate Results
- Gate type used (Personal Production / Commercial)
- Confidence score (out of 35) with breakdown
- Sufficiency score (out of 20) with breakdown
- Verdict (PASS / FAIL)

### 6. Evidence Summary
- Types of evidence captured (screenshots, test records, founder confirmation)
- Version binding — which version of the software was the evidence captured against?
- Any gaps in evidence and rationale for acceptance

### 7. Domain Contribution
- Which domain(s) does this project validate?
- What specific capabilities were exercised?
- What remains untested in this domain?

## Submission Process

1. Fork this repository
2. Create a new directory in `/evidence-packets/` named `{domain}-{project-name}/`
3. Include all packet sections as markdown files
4. Submit a pull request with a description of the project and its validation contribution

## Review Criteria

Evidence packets are reviewed for:
- Completeness — all seven sections present
- Honesty — claims match evidence, no overclaiming
- Evidence quality — Proven status backed by founder verification, not just system testing
- Gate integrity — release gate was run with full criteria, not abbreviated

Packets that overclaim or present system self-testing as founder verification will be returned for correction.
