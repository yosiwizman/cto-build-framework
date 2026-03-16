# Untested Domains

These domains have no field evidence from projects built under the CTO Build Framework governance. Some have governance doctrine designed; others have no specific documentation yet.

## Domains with Doctrine Designed

These domains have governance mechanisms documented in the framework (domain overlays, specialist review integration, evidence requirements) but no real project has exercised them.

### Authentication / Authorization
- **Doctrine:** Domain overlay designed covering session management, role-based access, password handling, OAuth flows
- **What would validate:** A project with login, session persistence, and role-based access that passes the full governance loop

### Backend / API / Database
- **Doctrine:** Architecture patterns documented for server-side logic, REST/GraphQL endpoints, SQL/NoSQL persistence
- **What would validate:** A project with a backend API and database that passes the full governance loop

### Payment Systems / Compliance
- **Doctrine:** PCI overlay designed covering card data handling, tokenization requirements, compliance evidence
- **What would validate:** A project processing payments with PCI compliance review that passes the governance loop

### Production Deployment / Runtime
- **Doctrine:** Deployment governance designed covering environment management, rollback in production, monitoring
- **What would validate:** A project deployed to production infrastructure that passes the governance loop

### CI / Branch / Merge Governance
- **Doctrine:** Branch governance designed covering merge approval, CI pipeline integration, automated checks
- **What would validate:** A project using CI/CD pipelines under governance that passes the loop

### Swarm / Parallel Execution
- **Doctrine:** Multi-agent orchestration designed covering parallel task execution, conflict resolution, state synchronization
- **What would validate:** A project using parallel AI agents under governance that passes the loop

## Domains with No Specific Doctrine

These domains have no governance documentation designed yet. Validation would require both designing the domain-specific governance and exercising it through a real project.

### External Integrations (Third-Party APIs)
- **Status:** No specific doctrine
- **Gap:** API consumption patterns, rate limiting governance, failure handling for external dependencies

### Real-Time / Event-Driven Systems
- **Status:** No specific doctrine
- **Gap:** WebSocket/SSE governance, event ordering, state synchronization under governance

### VoIP / Telephony Systems
- **Status:** No specific doctrine
- **Gap:** Voice call governance, SIP/WebRTC integration, carrier compliance

### AI Integration / LLM Workflows
- **Status:** No specific doctrine
- **Gap:** LLM-in-the-loop governance, prompt management, output validation, cost governance
