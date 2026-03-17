# Contributing to the CTO Build Framework

This repository tracks a live validation program for the CTO Build Book's governance methodology. Contributions are welcome under the following guidelines.

## Types of Contributions

### Validation Experiments

If you build a project under this governance in an untested domain and it passes the release gate, you can submit an evidence packet to expand the proof boundary.

**Requirements:**
- The project must have been scoped, approved, and built under the full governance loop
- All MUST requirements must have reached Proven status with founder verification
- The release gate must have been executed with a passing verdict
- An evidence packet must be prepared following the format in `validation/templates/evidence-packet-template.md`

**Process:**
1. Fork this repository
2. Add your evidence packet to `validation/evidence-packets/`
3. Update the relevant domain status in `/validation/`
4. Submit a pull request with a clear description of the project, domain, and evidence

### Governance Improvements

Proposed changes to the governance model itself (core loop, release gates, rollback protocol, audit separation) require:
- Clear rationale for the change
- Identification of all affected components
- Risk assessment — what could this change break?
- Evidence or reasoning that the change improves governance rather than weakening it

### Documentation Corrections

Factual errors, terminology inconsistencies, broken references, and formatting issues can be submitted as standard pull requests without the evidence requirements above.

## What We Do Not Accept

- Claims without evidence
- Domain status changes without corresponding evidence packets
- Governance changes that weaken evidence requirements
- Marketing language or promotional content

## Code of Conduct

This is an engineering governance repository. Contributions should be precise, evidence-based, and focused on improving the validation program. Disagreements are resolved through evidence, not opinion.
