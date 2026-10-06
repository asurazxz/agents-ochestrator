# Proposed architecture

Status: design direction; technology choices and interfaces are not finalized.

## Components

| Component | Responsibility |
| --- | --- |
| Hosted web application | Projects, invitations, context browsing, proposal review, and history |
| Shared context service | Project membership, approved revisions, proposals, and audit records |
| MCP integration | Agent tools for retrieving context and submitting proposals |
| Shared contracts | Consistent context, proposal, membership, and revision representations |
| Optional device connector | Session update delivery and later remote worker execution |

## Context flow

An authenticated agent retrieves approved context for a stable project ID. It records the revision used for its task. Discoveries become proposals referencing their starting revision. A project member reviews a proposal; approval produces a new revision with attribution. Other sessions fetch changes and explicitly adopt relevant updates.

## Minimum capabilities

- Retrieve approved project context and changes since a known revision.
- Submit an update proposal with its base revision and affected context.
- List and review proposals through the web application.
- Record acceptance, rejection, revisions, and the reviewing human.

Exact API routes, MCP tool names, schemas, and storage models will be selected during implementation planning.

## Recommended deployment and stack

Use a TypeScript workspace with React/Vite for the dashboard, Node.js/Fastify for the service, PostgreSQL with Drizzle for persistence, Better Auth for authentication, and the official MCP TypeScript SDK for agent tools. Serve the built dashboard and API from one application service initially. Package the application and database with Docker Compose; add an optional HTTPS proxy or tunnel separately.

These are recommendations, not finalized dependencies. See [technology stack](TECH_STACK.md) and [hosting](HOSTING.md). The current directories are placeholders; a backend service directory will be introduced during implementation planning.

## Scale and durability

Keep durable context, membership, reviews, and revision history in PostgreSQL. Approval must be transactional, with concurrency checks against the proposal's base revision. Use indexed project/revision lookups, pagination, bounded connection pools, and relevant-context retrieval.

Begin with a single deployment. Increase resources based on measured load; later separate database hosting and add application replicas. Streaming connections then need reconnection and shared event delivery. Remote orchestration will require durable task state, worker leases, cancellation, and reconciliation of uncertain runs.

## Export and acknowledgment

Recommend exporting approved context as Markdown without credentials or private transcripts. Track retrieval separately from explicit session acknowledgment. Acknowledgment means the session received the revision, not that the model complied with every instruction.

## Boundaries

Project membership must be checked for every read and write. Provider credentials remain local to the teammate's device. Proposed text and worker output are untrusted contributions, not authorization to execute commands.

The context service owns approved context; generated local files are snapshots. Git owns code history. A context revision and a code commit identify different things and should be recorded separately.

## Client integration

MCP provides retrieval and proposal tools, but does not by itself guarantee that an agent calls them at startup or after an update. Instructions can establish a working routine; a connector or controlled session interface may be needed for stronger automation. Prototype and document actual client behavior before making adoption guarantees.

## Future orchestration

Add an authenticated task queue and opt-in device workers after deciding the release scope. The orchestrator plans and reviews work; the service retains durable task records. Each worker controls its local execution permissions.
