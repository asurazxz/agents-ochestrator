# Existing solutions and product viability

Reviewed: 2026-10-06 (Asia/Singapore).

## Evidence boundary

This assessment uses primary product documentation, public READMEs, and license text. No competitor was installed, benchmarked, or tested with two devices. Marketing claims are described as documented capabilities. An unestablished feature is not proof that the feature does not exist. Prices, licensing, repositories, and supported clients can change.

## Comparison

| Solution | Documented overlap | Distribution/cost findings | Gap or unanswered question |
| --- | --- | --- | --- |
| threadctx | Repo-scoped MCP memory writes/queries, team cloud mode, instruction-file setup, and a memory dashboard | Public MCP client is MIT. Local mode is free; hosted team tiers exist. Website advertises self-hosting. | Direct memory writes are documented; the proposed pending/review/approved-revision/acknowledgment lifecycle was not established. A deployable backend was not verified in the linked public client repository. |
| Phorvec | Shared decisions/conventions, context branches and snapshots, conflict detection, audit records, and local embeddings | Website describes closed-source signed binaries. Central Team hosting is listed at US$49/project/month. | Significant functional overlap, but distribution/cost differ from our goals. Exact human review and session acknowledgment behavior was not tested. |
| MCP Agent Mail | Identities, inboxes, searchable threads, and advisory file reservations across coding clients | Public source, but current license is MIT with an additional OpenAI/Anthropic restriction. | Coordination is not proof of the proposed approved-context lifecycle. Advisory reservations do not enforce execution locks. Licensing is not standard MIT. |
| IM.codes | Self-hosted server/device daemons, shared memory, multiple providers, messaging, collaborative access, and supervised execution | MIT license; self-hosting is recommended. Deployment and optional model use have operating costs. | Closest broad overlap. README explicitly says project/workspace shared context is still under development and not fully production-tested. Exact review/version/adoption semantics remain unverified. |
| Agent Orchestrator | Desktop workspace for agent sessions, isolated Git branches/worktrees, and task-to-review/merge tracking | Apache-2.0 license; local agent and runtime costs remain separate | Local workspace is the documented focus. Independently owned devices sharing our exact approved-context workflow was not established. |

## Primary sources

- threadctx: [public MCP repository](https://github.com/threadctx-dev/threadctx-mcp), [product and hosted tiers](https://threadctx.dev/), [client license](https://github.com/threadctx-dev/threadctx-mcp/blob/main/LICENSE). The public README points to a relative `../cloud/README.md`; this review did not verify that backend's public availability or a working deployment.
- Phorvec: [features and closed-source distribution](https://www.phorvec.com/), [team hosting](https://www.phorvec.com/teams), [pricing](https://www.phorvec.com/pricing).
- MCP Agent Mail: [README](https://github.com/Dicklesworthstone/mcp_agent_mail), [current license](https://github.com/Dicklesworthstone/mcp_agent_mail/blob/main/LICENSE). Treat the rider as a separate licensing constraint; do not present it as standard MIT or assume unrestricted reuse.
- IM.codes: [README and self-hosting](https://github.com/im4codes/imcodes), [license](https://github.com/im4codes/imcodes/blob/master/LICENSE). Its README describes both shared context and supervised execution; approval-like functionality is not exclusive to our proposal.
- Agent Orchestrator: [README](https://github.com/OrchestratorInc/agent-orchestrator), [license](https://github.com/OrchestratorInc/agent-orchestrator/blob/main/LICENSE).

## Proposed differentiation

Build a focused, fully self-hostable review workflow for project context: proposals with diffs, human approval, immutable approved revisions, explicit session acknowledgment, provenance, and Markdown export. Acknowledge competitors' existing memory, review, branching, and orchestration capabilities; do not claim that individual features are novel.

Core storage/review/retrieval should require no mandatory inference service. A complete backend and dashboard under a standard open-source license would make self-hosting auditable and reproducible. The specific license remains undecided.

## Validation before a full build

Use threadctx and IM.codes as initial comparison baselines, subject to actual self-hosting availability and licenses:

1. Connect two devices to the same project context.
2. Submit a changed decision without making it approved context immediately.
3. Review and approve it as a human, recording attribution.
4. Have the other session compare against its prior revision, retrieve the approved change, and explicitly acknowledge delivery.
5. Submit a contradictory proposal and require resolution.
6. Export approved knowledge and verify whether core operations require additional model inference or paid services.

If a suitable existing tool satisfies this workflow with easy, fully open-source self-hosting, contributing to it may be preferable. Otherwise, the focused workflow is a credible project to publish. Adoption and novelty are hypotheses until tested with real teammates. Recommend context first and remote orchestration later; this remains a release-scope recommendation.
