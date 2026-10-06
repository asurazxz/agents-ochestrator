# Proposed roadmap

## 0. Validate integration and settle implementation choices

Review the [recommended stack](TECH_STACK.md) and choose the implementation details. Compare the [existing solutions](COMPETITORS.md) against the review/version workflow before committing to a full build. Verify context retrieval and proposal submission with supported Codex and Claude Code versions. Test fresh-session loading separately from mid-session updates. Decide whether orchestration is a later milestone.

Acceptance: A documented compatibility matrix and an agreed implementation design, with unsupported automation clearly identified.

## 1. Shared project memory

Implement projects, invitations, membership, initial context, proposals, member review, revisions, and history. Provide a small web interface and MCP retrieval/proposal tools. Package a self-hosted deployment and document installation, upgrade, migration, backup, and restore. Recommend Markdown export as part of the first usable release.

Acceptance: A laptop and desktop connect through the existing Twingate setup to the same server. One proposes a changed decision, a human approves it, and the other retrieves that approved revision. Pending proposals remain separate. A nonmember cannot read or modify the project. Core storage, review, and retrieval need no additional inference service.

## 2. Version-aware session continuity

Implement the accepted sync policy, adopted-revision tracking, changes since a baseline, stale proposal handling, and offline snapshots if included in the final design.

Acceptance: Sessions can identify stale context and display changes from their prior revision; contradictory proposals require resolution; cached context is labeled; downloading alone never counts as adoption. Explicit acknowledgment records delivery without implying model compliance.

## 3. Opt-in remote delegation

If selected, implement device registration, availability, bounded assignments, owner acceptance, isolated workers, and durable results.

Acceptance: A coordinator delegates to a second device and receives a reviewable result. Offline devices and uncertain runs do not cause silent duplicate execution. The owner can decline or stop work.

## 4. Optional automation

Consider automatic task acceptance within owner-defined limits and stronger session update delivery after manual workflows are proven.

Acceptance: Automation respects project and device permissions, reports failures, and preserves review history.

## Verification principles

Test membership isolation, proposal review, revision conflicts, client adoption, and worker failure handling at their relevant milestones. Add build and test commands after the stack is selected. Documentation scaffolding does not count as implementation of these milestones.

Public deployment is optional after private testing. Follow the [hosting guide](HOSTING.md); public access is not a prerequisite for cross-device behavior. Benchmark load and confirm backup restoration before making capacity or durability claims.
