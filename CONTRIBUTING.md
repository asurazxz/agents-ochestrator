# Team workflow

## Before starting

Read the shared agent instructions and current project status. Agree on task ownership through the team's chosen issue tracker or project discussion. A hosted ownership mechanism is not implemented yet.

Follow the accepted self-hosting and open-source goals. The [stack](docs/TECH_STACK.md) is recommended, not finalized. Review the [competitor assessment](docs/COMPETITORS.md) before claiming a feature is unique and the [GitHub guide](docs/GITHUB_SETUP.md) before repository setup.

Check the task's dependencies, accepted decisions, and starting code revision. Keep unfinished local work separate from the team's agreed context.

## Sharing knowledge

Use `docs/templates/CONTEXT_PROPOSAL.md` to propose a new instruction, discovery, or decision. State the previous version or decision, evidence, and affected tasks. Proposal storage and review tooling remain to be implemented; for now, use the team's review channel or explicitly requested repository review.

Any project member may approve or edit a proposal, including one submitted by their own agent. Record the approving human and rationale in the accepted decision record. Publishing an approved context update does not merge code or authorize remote execution.

## Changes and reviews

Keep contributions focused and include relevant verification. Use branches and pull requests when available; this scaffold does not configure a remote or change the surrounding repository. Never stage unrelated parent-repository changes.

Do not commit credentials, private transcripts, or local agent caches. Do not claim a proposal is accepted without human confirmation.

## Handoffs

Summarize the result, code revision if applicable, context used, verification, remaining work, and blockers. Use `docs/templates/HANDOFF.md`. Other agents should be able to resume without access to your private conversation.

## Development commands

No application commands exist yet. Once a stack is selected, document installation, development, linting, and test commands in `README.md` and the appropriate component README.
