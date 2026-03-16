# Evidence Packet — Template

> **Instructions:** Copy this file to `validation/evidence-packets/{domain}-{project-name}.md`. Fill every field. This packet is the canonical proof record for a domain claim. Incomplete packets do not count as evidence.

---

## Packet Metadata

| Field | Value |
|-------|-------|
| Claim being proven | |
| Domain | |
| Project | |
| Software version at time of evidence capture | |
| Date evidence captured | YYYY-MM-DD |
| Evidence captured by | |
| Packet prepared by | |
| Packet version | |

---

## 1. The Claim

State the exact claim this packet supports.

_Be precise. "The CTO Build Framework governance loop works for client-side CRUD applications" is a claim. "The framework works well" is not._

---

## 2. What This Claim Does NOT Cover

State explicitly what is out of scope for this claim.

_Every claim has limits. Stating them here is a strength, not a weakness. It prevents future overclaiming against this packet._

---

## 3. Artifact List

List every artifact that supports this claim.

| # | Artifact | Type | Description | File / Location |
|---|---------|------|-------------|-----------------|
| 1 | | Screenshot / Log / Test record / Gate result / Founder confirmation | | |
| 2 | | | | |
| 3 | | | | |

_Do not reference artifacts that do not exist. If an artifact is missing, mark the packet as incomplete._

---

## 4. Requirement Evidence

For each MUST requirement, list the evidence and verification status.

| Requirement | Truth State | Evidence Artifact | Verified By | Notes |
|-------------|-------------|------------------|-------------|-------|
| | Proven / Tested / Implemented / Planned | | Founder / Reviewer / AI (if AI: explain why accepted) | |

_"Tested" means the system confirmed it. "Proven" means a human verified it independently. These are not the same._

---

## 5. Founder Verification

**Did the founding operator independently verify the software?**

- [ ] Yes — verified on the following device(s):
- [ ] Partial — verified some requirements (list which):
- [ ] No — explain why not:

**Founder verification notes:**

---

## 6. Reviewer Verification

**Was this packet reviewed by a party other than the builder?**

- [ ] Yes — reviewer: ___ , date: ___ , verdict file: ___
- [ ] No — explain why not:

---

## 7. Release Gate Results

| Field | Value |
|-------|-------|
| Gate type used | Personal Production / Commercial |
| Confidence score | / 35 |
| Sufficiency score | / 20 |
| Gate verdict | PASS / FAIL |
| Gate record location | |

---

## 8. Proof-Boundary Note

**What does this evidence prove?**
**What does this evidence NOT prove?**

_Write this in plain English. This note travels with the packet and governs how the claim can be used in future work._

---

## 9. Unresolved Limits

List any gaps, conditions, or known weaknesses in this evidence.

| Limit | Impact | Status |
|-------|--------|--------|
| | | Accepted / Needs follow-up |

---

## 10. Packet Status

- [ ] Complete — all sections filled, artifacts on file, ready for ledger update
- [ ] Incomplete — missing: (list what's missing)
- [ ] Superseded — replaced by: (link to newer packet)

---

_This template is part of the CTO Build Framework validation infrastructure. Do not modify the template — copy it for each new evidence packet._
