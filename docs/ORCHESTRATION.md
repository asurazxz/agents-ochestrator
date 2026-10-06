# Proposed remote orchestration

Status: requested feasibility direction; inclusion in the first release is undecided.

## Goal

Let one teammate's agent coordinate dedicated worker sessions on other teammates' devices. A shared service retains assignments and results so coordination does not depend on one device holding all project state.

## Recommended execution flow

1. Each teammate opts a device into a project and chooses allowed work and availability.
2. The coordinating agent submits a bounded task with an approved context revision, starting code commit, and completion criteria.
3. The service queues the task for an eligible device.
4. The teammate accepts it, or a previously configured acceptance policy permits it.
5. The connector launches a dedicated worker session in an isolated working copy.
6. The worker returns a summary, verification results, and a branch or patch.
7. The coordinator reviews results and proposes integration through the normal code review process.

## Required controls

- Device owners retain local execution permissions and credentials.
- Context approval does not authorize remote execution.
- Do not inject assignments into an unrelated active personal session.
- Offline devices leave tasks queued. Do not assume they are available.
- Track task identity, attempts, cancellation, and results. An expired connection does not prove execution stopped; resolve uncertain runs before reassigning.
- Enforce project membership for task submission, pickup, and result access.
- Do not automatically merge or publish worker code in the initial design.

## Feasibility basis

Codex documents noninteractive execution and an App Server for persistent sessions, streamed events, and approval handling. Claude Code documents programmatic execution and structured results. These are building blocks for custom worker adapters, not proof of a complete cross-device implementation.

Integration spikes must verify supported client versions, authentication, cancellation, isolated working copies, and permissions. Do not promise subscription compatibility without testing the intended supported setup.

## Suggested sequence

Shared context first, teammate-accepted delegation second, and optional automatic acceptance later. This sequence remains a recommendation until the user chooses orchestration scope.
