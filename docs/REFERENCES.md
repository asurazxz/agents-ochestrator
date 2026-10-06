# References

Reviewed during project planning and the documentation update on 2026-10-06 (Asia/Singapore). Provider capabilities, prices, and licenses can change; recheck these primary sources before implementation or release.

## Agent integration

- [Claude Code project memory](https://code.claude.com/docs/en/memory): shared instruction files, imports, and machine-local automatic memory.
- [MCP architecture](https://modelcontextprotocol.io/docs/learn/architecture): connecting clients to tools and context.
- [MCP tools specification](https://modelcontextprotocol.io/specification/2025-11-25/server/tools): client/model tool invocation behavior.
- [MCP Agent Mail](https://github.com/Dicklesworthstone/mcp_agent_mail): an existing coordination layer with messaging and advisory file reservations; not tested in this project.
- [Codex integration options](https://developers.openai.com/blog/codex-as-a-platform): noninteractive execution, SDK, and App Server.
- [Codex App Server](https://learn.chatgpt.com/docs/app-server): session control, events, and approvals.
- [Claude Code programmatic execution](https://code.claude.com/docs/en/headless): noninteractive runs, structured results, and session continuation.

## Recommended stack and operations

- [Vite](https://vite.dev/guide/): frontend development and production builds.
- [Fastify TypeScript support](https://fastify.dev/docs/latest/Reference/TypeScript/): backend framework integration.
- [Drizzle transactions](https://orm.drizzle.team/docs/transactions): atomic database operations.
- [Better Auth Fastify integration](https://better-auth.com/docs/integrations/fastify): self-hosted authentication integration.
- [Better Auth organizations](https://better-auth.com/docs/plugins/organization): membership and invitation capabilities to evaluate.
- [MCP SDKs](https://modelcontextprotocol.io/docs/sdk): official implementation options.
- [Docker Compose in production](https://docs.docker.com/compose/how-tos/production/): single-server deployment guidance.
- [Caddy automatic HTTPS](https://caddyserver.com/docs/automatic-https): optional reverse proxy and certificate management.

## Hosting

- [Cloudflare Tunnel](https://developers.cloudflare.com/tunnel/): availability on all plans and outbound host connections.
- [Named tunnel setup](https://developers.cloudflare.com/tunnel/get-started/): published-hostname prerequisites.
- [Quick Tunnels](https://developers.cloudflare.com/tunnel/get-started/quick-tunnels/): temporary URLs, concurrent-request limits, and streaming restrictions.

Initial testing through Twingate is an accepted project preference, not a provider configuration tested during this research.

## Existing solutions

- [threadctx public client](https://github.com/threadctx-dev/threadctx-mcp) and [product site](https://threadctx.dev/).
- [Phorvec features](https://www.phorvec.com/), [teams](https://www.phorvec.com/teams), and [pricing](https://www.phorvec.com/pricing).
- [MCP Agent Mail license](https://github.com/Dicklesworthstone/mcp_agent_mail/blob/main/LICENSE): nonstandard rider in the current license.
- [IM.codes](https://github.com/im4codes/imcodes): self-hosted agent sessions, memory, and coordination.
- [Agent Orchestrator](https://github.com/OrchestratorInc/agent-orchestrator): local workspace and isolated agent work.

See [competitor assessment](COMPETITORS.md) for evidence limits and licensing links. No competitor installation or two-device compatibility test has been performed.

## GitHub preparation

- [Importing locally hosted code](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github?platform=linux): empty repository guidance.
- [Licensing a repository](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository): public visibility and reuse permissions.

These sources establish integration building blocks, not guaranteed compatibility with every subscription, client version, or device environment.
