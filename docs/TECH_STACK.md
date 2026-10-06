# Recommended technology stack

Status: recommendation, not an accepted implementation decision. No dependencies are installed.

## Selection goals

Easy self-hosting, fully open-source distribution, minimal recurring costs, and maintainability for a small team. Avoid mandatory paid infrastructure or inference for basic context storage, review, and retrieval.

## Suggested components

| Layer | Recommendation | Purpose |
| --- | --- | --- |
| Language/runtime | TypeScript and a supported Node.js LTS release | Shared types across service, UI, and connector |
| Dashboard | React with Vite | Projects, context, proposal review, revision history |
| API/service | Fastify | Authentication, authorization, shared context, agent-facing operations |
| Database | PostgreSQL | Membership, proposals, approved revisions, audit records |
| Persistence tooling | Drizzle ORM and migrations | Typed queries and versioned schema changes |
| Authentication | Better Auth | Self-hosted login; evaluate organization support for invitations |
| Agent integration | Official MCP TypeScript SDK | Retrieval, revision changes, and proposal submission |
| Device connector | Node.js CLI | Agent setup; later opt-in task execution |
| Workspace | pnpm workspaces | Share contracts and develop components together |
| Distribution | Docker Compose and versioned container images | Reproducible local/server deployment |
| Verification | Vitest and Playwright | Service behavior and complete browser workflows |
| Public HTTPS, optional | Caddy or a named Cloudflare Tunnel | Reach the application from outside the private network |

Vite produces a frontend build that the application service can serve. Better Auth documents [Fastify integration](https://better-auth.com/docs/integrations/fastify) and [organization capabilities](https://better-auth.com/docs/plugins/organization), but project membership must still be checked in application operations. Drizzle supports [transactions](https://orm.drizzle.team/docs/transactions). MCP publishes [official SDK guidance](https://modelcontextprotocol.io/docs/sdk).

Select exact versions and verify compatibility during implementation planning. Do not copy version numbers from undated examples. No backend application directory or package manifests exist yet.

## Why this arrangement

The product is an authenticated dashboard plus a service used by agents and, later, device workers. One language reduces contract drift. Standard PostgreSQL and containers keep deployment portable. Initially serve the dashboard and API from one application service and origin to simplify deployment and browser authentication.

## Recommended interfaces

Keep browser operations and MCP tools backed by the same context/review logic. Shared contracts should cover stable project identity, proposals, approved revisions, and acknowledgment. Exact API routes, schemas, transports, and client authentication remain to be designed.

Do not confuse browser cookies, application access tokens, and local LLM-provider credentials. Teammates retain their provider credentials. Verify supported client authentication before claiming compatibility.

## Inference and costs

Existing coding agents can draft proposals. Core storage, review, version history, and retrieval should work without a server-side model. Automatic summarization, embeddings, or commit capture are optional later capabilities with explicit cost and provider requirements. Existing subscription usage limits still apply.

## Scaling sequence

1. Run one application instance and PostgreSQL on a server. A 2-core/4-GB machine is an initial benchmark hypothesis, not a capacity guarantee.
2. Measure request latency, database query time, payload sizes, connections, and resource utilization. Use indexed project/revision queries, pagination, and bounded connection pools.
3. Make approval atomic and check the proposal base revision within the transaction. Keep durable shared state out of process memory.
4. Move the database to dedicated or managed hosting as needed, then add stateless application replicas and load balancing. Streaming sessions require reconnection handling and shared delivery across instances.
5. Add a durable queue, worker leases, cancellation, and uncertain-run reconciliation for orchestration. Devices execute agent work; the hosted service coordinates it.

Introduce a cache, dedicated queue service, or object storage only when measured load or actual artifact requirements justify it. Ordinary context records can start in PostgreSQL. Multiple replicas improve service capacity but do not make a single database or home server highly available.

## Operational release requirements

Document installation, configuration, upgrades, migrations, backups, and restore. Verify restore before making durability claims. Pin release artifacts and check dependency licenses before distribution. These are future release requirements, not completed work.
