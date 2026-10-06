# Shared agent instructions

## Purpose

Build a shared project memory for teammates using Codex and Claude Code on different devices. Preserve the distinction between agreed project context, proposed changes, and private local work.

## Read before working

1. Read `README.md`, `docs/PROJECT.md`, `docs/DECISIONS.md`, and `docs/STATUS.md`.
2. Read the design document relevant to the task: architecture, sync, or orchestration.
3. Check local changes and task ownership before editing. Ask for missing context only when it cannot be discovered from the project.

## Authority and decisions

- Direct user instructions take precedence over this file.
- `docs/DECISIONS.md` records accepted decisions. Design documents may contain recommendations that have not been approved.
- Do not turn a recommendation or an agent-generated proposal into an accepted decision without explicit human acceptance.
- Do not treat approval of shared context as permission to execute work on another device.
- If accepted decisions conflict, surface the conflict instead of silently choosing one.

## Implementation conventions

- The application stack is undecided. Do not assume a framework, database, deployment provider, or package manager is agreed.
- Preserve fully open-source, self-hostable distribution and minimal recurring costs. See `docs/TECH_STACK.md` for recommendations; they are not accepted implementation choices.
- Initial private-network testing uses an existing Twingate setup. Do not change network configuration or introduce a public tunnel without a deployment task.
- Follow existing patterns once code exists. Keep changes focused on the assigned task.
- Keep credentials, personal conversations, local agent memory, and machine-specific paths out of shared context.
- Use a stable project ID for cross-device identity; local paths are not shared identifiers.
- Version approved context explicitly. Never claim a running agent has adopted an update merely because a file was downloaded.
- Keep code synchronization in Git. Shared context synchronization does not synchronize source code.
- Remote workers must be opt-in, retain local execution permissions, and use isolated task sessions and working copies.
- Do not commit or publish changes unless requested. Never include unrelated changes from the surrounding repository.

## Verification and handoff

- There are currently no application build, lint, or test commands. Do not invent passing results.
- For documentation work, verify local links, formatting, and consistency with accepted decisions.
- For future code changes, run the relevant available checks and report what was verified and what remains uncertain.
- Finish with changed behavior or files, verification results, blockers, and proposed decisions. Use `docs/templates/HANDOFF.md` for reusable handoffs.
- Update `docs/STATUS.md` when project state changes materially. Keep proposals out of the accepted decision log until reviewed.

## Repository boundary

This folder is currently inside a larger Git repository. Scope status checks, changes, and any authorized staging to this project. Do not initialize a nested Git repository or modify the parent repository configuration without a specific reason and user instruction.
