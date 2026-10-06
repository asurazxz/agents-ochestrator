# Agents Orchestrator

A self-hostable shared project memory for teams using different coding agents on different devices.

## Problem

Teams bring their own Codex, Claude Code, and other agent subscriptions to a project. Instructions, decisions, and handoffs stay in separate sessions, causing inconsistent work and manual consolidation.

## Intended product

A shared workspace with invitations, approved project context, and agent integrations. One operator hosts the service; teammates connect their existing agents. Agents retrieve agreed instructions and decisions, then propose discoveries for human review. Any project member can approve or edit proposals, with attribution and history.

## Product direction

Target fully open-source distribution, easy self-hosting, and minimal recurring costs. The proposed differentiator is human-reviewed, versioned context with explicit session acknowledgment and portable Markdown export. Shared agent memory already exists; the competitor review does not establish that these features are unique.

Initial testing will use two devices and a shared server reachable through an existing Twingate network. Cloudflare Tunnel is an optional later access method, not a product requirement.

## Current status

Documentation and directory scaffold only. There is no running application, configured MCP server, database, authentication service, or remote worker. No dependencies or application stack have been selected. No build or application test commands exist yet.

## Start here

- [Project brief](docs/PROJECT.md): goals, agreed preferences, and open choices.
- [Architecture](docs/ARCHITECTURE.md): proposed components and boundaries.
- [Technology stack](docs/TECH_STACK.md): recommended frameworks, packaging, and scaling approach.
- [Hosting guide](docs/HOSTING.md): who hosts, how teammates connect, and private/public access options.
- [Existing solutions](docs/COMPETITORS.md): dated capability, licensing, and cost comparison.
- [GitHub setup](docs/GITHUB_SETUP.md): repository creation and separation from the parent repository.
- [Context syncing](docs/SYNC.md): versions, adoption, and conflict handling.
- [Orchestration](docs/ORCHESTRATION.md): proposed remote delegation extension.
- [Roadmap](docs/ROADMAP.md): implementation sequence and acceptance criteria.
- [Decisions](docs/DECISIONS.md): accepted decisions and their rationale.
- [Team workflow](CONTRIBUTING.md): contribution and agent handoff practices.
- [Project status](docs/STATUS.md): current work and next steps.

## Directory layout

```text
apps/                 Intended web application and device connector
packages/             Intended shared contracts and MCP integration
docs/                 Project context, designs, and status
docs/templates/       Proposal, decision, and handoff templates
AGENTS.md             Canonical shared agent instructions
CLAUDE.md             Imports the shared instructions for Claude Code
```

## Initial onboarding

Read `AGENTS.md`, `docs/PROJECT.md`, `docs/DECISIONS.md`, and `docs/STATUS.md`. These files are the initial project context; they do not implement the future hosted sync service. Record new proposals separately from accepted decisions.

Fully open-source distribution is the intended model. The license remains undecided; public source visibility alone is not an open-source license. No deployment or installation commands are available for this product yet.
