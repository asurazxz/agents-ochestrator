# Project brief

## Audience and problem

Small teams working on group projects and hackathons, with each teammate using their own coding agent on their own device. Agent sessions lose shared instructions and decisions, and teammates manually consolidate inconsistent outputs.

## Agreed preferences

- Prioritize shared project context and decisions.
- Start with Codex and Claude Code integrations.
- Use a hosted workspace with project invitations.
- Require human review before proposed updates become approved context.
- Allow any project member to approve or edit proposals, including proposals from their own agent.
- Record approval attribution and change history.
- Target fully open-source distribution and easy self-hosting.
- Keep recurring costs as low as practical.
- Use the existing Twingate private network for initial laptop/desktop/server testing.

A hosted workspace means one shared service that teammates connect to. It does not require a vendor-managed subscription or a backend installation on every device.

## First success criterion

A teammate starts a fresh agent session on another device and receives the latest approved project context without someone manually briefing them.

## Recommended initial scope

Project creation and membership, context retrieval, update proposals, review, and version history. Shared context consists of instructions, accepted decisions, and relevant discoveries or handoffs.

Git-style version tracking and remote orchestration have been discussed as recommendations, not yet accepted implementation decisions.

## Proposed positioning

Human-reviewed, versioned project context with explicit session acknowledgment, clear provenance, and Markdown export. Basic shared memory and agent messaging have existing alternatives; this is a focused workflow proposal, not a claim of category novelty. See [competitor comparison](COMPETITORS.md).

Core storage, review, and retrieval should not require additional model inference. Optional summarization or capture could incur provider usage charges. This is a design recommendation, not implemented behavior.

## Open choices

- Application language, frameworks, database, and hosting provider.
- Authentication and invitation mechanism.
- Supported client versions and the degree of mid-session automation.
- Whether initial context ingestion is manual or imports repository files.
- Whether delegation belongs in the first release or a later milestone.
- Specific open-source license.

The [technology recommendation](TECH_STACK.md) and [hosting guide](HOSTING.md) document proposed choices without making them accepted decisions.

## Initial exclusions

Full private transcript synchronization, account credential sharing, replacement of Git code synchronization, and automatic merging of generated code are outside the recommended initial scope.

## Product boundary

The service shares selected project knowledge. Each teammate retains their own coding environment and credentials. Supported subscription authentication and client behavior must be verified before claiming compatibility.
