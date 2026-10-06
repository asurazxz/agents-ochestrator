# Proposed context synchronization

Status: recommended behavior, pending human acceptance and client feasibility checks.

## What is synchronized

Approved project instructions, accepted decisions, and selected discoveries or handoffs. Private conversations, provider credentials, and undocumented agent memory are not synchronization inputs.

## Baseline and revisions

Each session tracks the last shared revision it actually adopted. Compare remote changes against that revision, rather than comparing against an LLM's recollection. Fetching a revision and adopting it are separate events.

Represent adoption through explicit session acknowledgment after the revision is delivered into that session. Acknowledgment records delivery; it does not prove the model read every word or followed every instruction. Do not promise stronger guarantees than the client integration can establish.

## Recommended workflow

1. Retrieve approved context at session start and before each new task.
2. Show changes since the session's adopted revision.
3. Supply relevant updates to the agent and record adoption.
4. Submit local discoveries as proposals with a base revision.
5. Have a project member approve or edit the proposal.
6. Publish a new approved revision and make it available to other sessions.

Updates affecting an ongoing task should create a checkpoint for reconciliation. Downloading a new snapshot must not silently overwrite private work or be reported as agent adoption.

## Conflicting proposals

If the underlying context changed after a proposal's base revision, check whether it affects the same decision. Overlapping changes require explicit human resolution. Preserve both proposals and their review history; do not use last-write-wins for contradictory decisions.

## Offline behavior

A session may read its cached approved snapshot, clearly labeled with its revision and offline status. Locally drafted proposals remain pending until submitted and reviewed. Reconnecting fetches missing revisions and checks stale proposals before acceptance.

## Context and code

A shared context revision does not imply the local code is current. Record the code commit alongside the adopted context revision when relevant to a task or handoff. Use Git for code synchronization.

## Validation scenarios

- A fresh session on a second device retrieves the latest approved revision.
- An unapproved proposal never appears as accepted context.
- Fetching without delivery or acknowledgment does not advance adoption.
- Concurrent contradictory proposals require resolution.
- Reconnecting preserves local drafts and identifies stale context.
- Updates affecting active work are surfaced at a checkpoint.

## Portability

Recommend Markdown export of approved instructions and decisions, including revision and approval provenance. Export is a portable snapshot; importing or editing it must not silently overwrite the authoritative server state. Export and import details remain to be designed.
