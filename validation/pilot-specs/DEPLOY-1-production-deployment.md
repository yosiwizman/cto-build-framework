# Pilot Spec: DEPLOY-1 — Production Deployment / Runtime

**Type:** Validation pilot specification — pre-execution planning document
**Domain:** Production Deployment / Runtime
**Current status:** Untested (doctrine exists; no deployment exercised under governance)
**Date created:** 2026-03-18

---

## Purpose

Produce the first governed deployment of a project to a real production environment. This pilot proves that the governance loop handles environment control, deployment execution, runtime verification, and rollback — capabilities that separate "it works on my machine" from "it runs in production."

All current validated pilots are client-side applications with no production server. This pilot closes that gap.

---

## Current Proof Status

- Deployment governance doctrine exists
- No project has been deployed to a production environment under the governance loop
- No evidence packet, run log, or reviewer verdict exists for this domain
- The domain cannot be cited as field-tested until this pilot (or equivalent) completes

Reference: `validation/domain-matrix.md` row "Production Deployment / Runtime" and `validation/evidence-expansion-roadmap.md` Priority 6.

---

## Scope Boundary

**In scope:**
- Deployment of a working application to a real, publicly accessible production environment (cloud host, VPS, or equivalent — not localhost)
- Environment configuration documented and reproducible
- Deployment executed as a governed step with pre-deployment and post-deployment verification
- Post-deployment runtime verification: the application works in production as it did in development
- Rollback capability: the ability to revert to a known-good state if deployment fails
- At least one rollback test: deploy, verify, then execute rollback to confirm it works

**Out of scope:**
- CI/CD pipeline automation — that is a separate domain (CI governance)
- Zero-downtime deployment, blue-green, or canary patterns — future scope after basic deployment is proven
- Auto-scaling, load balancing, or multi-region deployment
- Infrastructure-as-code governance (Terraform, Pulumi, etc.) — future scope
- SSL/TLS certificate management as a governance domain — operational requirement but not the focus of this pilot
- Monitoring, alerting, or observability infrastructure — operational concern, not governance proof

**Dependency note:** This pilot naturally follows API-1 (backend). A backend project provides the deployment target. Running DEPLOY-1 without a backend project would require deploying a static site, which has lower governance complexity and weaker proof value.

---

## MUST Requirements

| ID | Requirement | Verification Method |
|----|-------------|-------------------|
| DEPLOY-1.01 | Application is deployed to a real production environment (not localhost) | Founder verification — access via public URL |
| DEPLOY-1.02 | Production environment configuration is documented | Configuration artifact on file |
| DEPLOY-1.03 | Deployment was executed as a governed step with explicit approval before execution | Run log entry showing pre-deployment checkpoint |
| DEPLOY-1.04 | Post-deployment verification confirms application functions correctly in production | Founder verification — test core functionality via production URL |
| DEPLOY-1.05 | At least one difference between dev and production environments is documented | Configuration artifact — e.g., database URL, environment variables, host settings |
| DEPLOY-1.06 | Rollback mechanism exists and is documented | Rollback procedure on file |
| DEPLOY-1.07 | Rollback was tested: application was reverted to a previous known-good state | Founder verification — execute rollback, confirm previous version is restored |
| DEPLOY-1.08 | Post-rollback verification confirms the rolled-back version functions correctly | Founder verification — test core functionality after rollback |

---

## Exclusions / Non-Goals

- This pilot does not prove CI/CD pipeline governance
- This pilot does not prove zero-downtime or advanced deployment strategies
- This pilot does not prove infrastructure-as-code governance
- This pilot does not prove multi-environment promotion chains (dev → staging → production)
- This pilot does not prove monitoring or alerting governance
- This pilot does not validate any domain beyond Production Deployment / Runtime

---

## Required Evidence Artifacts

| Artifact | Template | Filing Location |
|----------|----------|-----------------|
| Validation run log | `validation/templates/domain-validation-run-template.md` | `validation/runs/production-deployment-DEPLOY-1-[date].md` |
| Environment configuration record | No template — plain document | Embedded in or linked from run log |
| Rollback test record | No template — documented in run log | Part of run log |
| Evidence packet | `validation/templates/evidence-packet-template.md` | `validation/evidence-packets/production-deployment-DEPLOY-1-[date].md` |
| Reviewer verdict | `validation/templates/reviewer-verdict-template.md` | `validation/reviews/production-deployment-DEPLOY-1-review-[date].md` |

All artifacts must declare Artifact Class 3 (New Execution Artifact).

---

## Founder Verification Requirements

- Founder accesses the application via its production URL and confirms core functionality
- Founder reviews and approves the environment configuration before deployment
- Founder witnesses or executes the rollback test and confirms the previous version is restored
- Founder signs off on each MUST requirement individually in the evidence packet

---

## Release / Gate Criteria

The release gate must:
- Cover all 8 MUST requirements
- Produce a scored verdict (PASS / FAIL)
- Include explicit confirmation that the application was accessed in production (not localhost)
- Include explicit confirmation that rollback was tested and the previous version was restored

A PASS requires: all MUST requirements at Proven, environment configuration documented, rollback tested, and evidence packet filed.

---

## Specialist Review Requirements

None required at the current scope. Basic production deployment to a single environment does not trigger specialist review. If the deployment involves regulated data, healthcare infrastructure, financial systems, or government environments, specialist review requirements would apply based on the relevant domain overlay.

---

## Promotion Criteria

This domain may be promoted from Untested to Validated when:

1. This pilot (or equivalent) completes with a PASS gate verdict
2. All required evidence artifacts are filed
3. Reviewer verdict is filed
4. Independent re-execution proof is on file
5. `validation/domain-matrix.md` is updated in the same commit as the reviewer verdict
6. `validation/validation-ledger.md` is updated to reflect new status and artifact links

The domain remains Untested until all conditions are met.

---

_This is a pre-execution planning document. It does not constitute evidence of validation. Filing this spec does not change the domain's current status._
