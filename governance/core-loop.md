# Core Governance Loop

The CTO Build Framework operates on a single governance loop that applies at every project scale.

## The Six Phases

### Phase 1: Scope
Define what will be built with specific, testable requirements. Every requirement must be written as a verifiable statement — not a wish, a direction, or an aspiration. Requirements are classified as MUST (mandatory for release) or NICE (valuable but not blocking).

The scope also defines what is explicitly out of scope. This boundary is enforced throughout the build and checked at the release gate.

### Phase 2: Architecture
Approve a structural plan before any building begins. The architecture recommendation answers five questions the founder can evaluate without technical knowledge: Does it match the requirements? Is it as simple as possible? What are the risks? What's the fallback? Does the cost match constraints?

Architecture approval is a founder decision, not a technical rubber stamp.

### Phase 3: Build
Execute in small, independently testable slices. Each slice produces a specific, verifiable result. After each successful slice, a checkpoint is saved — a verified, recoverable state. If a future slice fails, the system rolls back to the last checkpoint rather than attempting to patch broken code.

The AI operates autonomously within approved boundaries. Thirteen categories of decisions require founder approval before proceeding.

### Phase 4: Verify
Capture evidence for every requirement. Evidence progresses through five truth states:

| State | Meaning |
|-------|---------|
| **Planned** | Requirement defined, no code exists |
| **Implemented** | Code exists, not tested |
| **Tested** | System checked its own work |
| **Proven** | Founder personally verified with evidence on file |
| **Honestly Claimable** | Evidence strong enough for public claims |

The system checking its own work (Tested) is necessary but not sufficient. The release gate requires founder verification (Proven) for every MUST requirement.

### Phase 5: Gate
Run a structured release gate that checks all requirements against documented evidence. The gate evaluates approximately twenty criteria grouped into six categories:

1. **Requirement verification** — Every MUST requirement at Proven or above
2. **System testing** — Diagnostics pass, no critical failures
3. **Drift check** — No unauthorized scope changes
4. **Blocker check** — No open blockers
5. **Evidence completeness** — Evidence record is complete and current
6. **Recovery availability** — Rollback path is documented and functional

The gate produces two scores:
- **Confidence score** (out of 35): How certain is the evidence that the software works?
- **Sufficiency score** (out of 20): How complete is the proof?

A gate verdict is PASS or FAIL. There is no "close enough."

### Phase 6: Release
Ship only what passes the gate. The release produces a permanent, documented record: what was verified, by whom, against which version, with what evidence. This record is the foundation for every claim about the software.

## Loop Invariants

The following properties are maintained at every phase:
- Evidence is version-bound (proof against one version says nothing about a changed version)
- The builder does not audit its own work without founder verification
- Scope changes require explicit approval through the change process
- Failure is contained to the current slice — it cannot infect previous verified work
- The founder makes all strategic decisions; the AI makes execution decisions within approved boundaries

## Loop Application by Project Class

| Class | Governance Layers | Example |
|-------|------------------|---------|
| Standard | Base loop only | Personal tools, CRUD apps, dashboards |
| Complex | Base loop + multi-session continuity | Backend APIs, database-backed apps |
| Domain-Heavy | Base loop + domain overlays + specialist review | Payments, security, healthcare |
| Specialist | Full governance stack + regulatory compliance | HIPAA, PCI, safety-critical |
