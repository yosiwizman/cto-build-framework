# Validation Roadmap

This document describes the staged plan for expanding the CTO Build Framework's proof boundary into new domains.

## Current State

The core governance loop is validated for Standard-class client-side web applications through two pilot projects. The proof boundary includes: CRUD operations, multi-page routing, search/filtering, form validation, responsive UI, and localStorage persistence.

## Expansion Principles

1. **One domain at a time.** Each validation effort targets a specific domain with specific evidence requirements.
2. **Real projects, not thought experiments.** Validation requires a real project through the full governance loop, not theoretical analysis.
3. **Evidence before claims.** A domain status changes only after evidence packets are submitted and reviewed.
4. **Incremental boundary expansion.** Each validated domain extends the proof boundary. No domain is "validated by association."

## Phase 1: Core Loop (COMPLETE)

**Status:** Validated
**Domains covered:**
- CRUD / local-state applications
- Client-side multi-page applications
- Search / filtering
- Form validation
- Responsive UI

**Evidence:** Two pilot projects (task tracker, contact manager), both passing release gates with all MUST requirements at Proven.

## Phase 2: Backend Foundation (NEXT)

**Target domains:**
- Backend / API services
- Database integration

**Validation approach:** Build a project with a Node.js or Python backend, REST API endpoints, and a SQL or NoSQL database under full governance.

**Evidence requirements:**
- API endpoints tested and founder-verified
- Database operations (CRUD) verified with real data
- Error handling verified for common failure modes
- Release gate passes with all MUST requirements at Proven

**Expected outcome:** Proof boundary extends to backend-first applications.

## Phase 3: Identity and Integration

**Target domains:**
- Authentication / authorization
- External integrations (third-party APIs)

**Validation approach:** Build a project with user login, session management, and at least one third-party API integration under full governance.

**Evidence requirements:**
- Login/logout flow verified by founder
- Session persistence verified across browser restart
- Third-party API integration verified with real responses
- Error handling for API failures verified
- Release gate passes

**Expected outcome:** Proof boundary extends to identity and integration patterns.

## Phase 4: Domain-Heavy Validation

**Target domains:**
- Payment systems / compliance
- Production deployment / runtime
- CI / merge governance

**Validation approach:** Build projects that exercise domain overlays and specialist review integration. Payment projects require PCI compliance review. Deployment projects require production infrastructure governance.

**Evidence requirements:**
- Domain overlay activated and constraints enforced during build
- Specialist review integrated where required
- Domain-specific evidence captured (PCI compliance, deployment logs, CI pipeline results)
- Release gate includes domain-specific criteria
- All MUST requirements at Proven

**Expected outcome:** Proof boundary extends to regulated and infrastructure domains.

## Phase 5: Advanced Patterns

**Target domains:**
- Real-time / event-driven systems
- Parallel agent swarms
- Multi-session continuity (full validation)
- VoIP / telephony
- AI / LLM workflows

**Validation approach:** These domains represent the furthest expansion of the proof boundary. Each requires designing domain-specific governance before it can be exercised.

**Evidence requirements:** Domain-specific — to be defined as each domain's governance doctrine is designed.

**Expected outcome:** Comprehensive proof boundary covering the majority of common software domains.

## Timeline

This roadmap is ordered by priority and feasibility, not by calendar dates. Each phase begins when the previous phase has at least one validated domain. The boundary expands through work, not through time passing.

Community contributions (via evidence packets) can accelerate any phase. A founder who builds and validates a payment system under governance, for example, advances Phase 4 regardless of whether Phase 3 is complete.
