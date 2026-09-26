# Current State

Snapshot date: 2026-09-26

## Source repository
`thecakeisalie05/Agentic-Studio`

## Current verified release
`v0.2.0-alpha.2` — Agentic Studio Alpha 0.2 — Hotfix 2.

Human verification:
- Windows installer works.
- Agentic Studio is discoverable through Windows Start/Search.
- Studio Chat works in the installed application.
- A message can be sent and a response is received.

Alpha.2 incorporated the Astra-compatible bundled Codex runtime update and keeps Studio Chat as the plain collaborative/read-only ChatGPT-labelled surface rather than a Work/Build mode.

## Implemented substrate
The current application has the important middle of the software-development loop:
- durable Missions and typed runtime packets;
- provider-neutral execution with deterministic Demo behavior;
- live OpenAI/Codex-backed execution;
- isolated managed Git worktrees;
- file modification and command execution;
- deterministic build/test validation;
- bounded retries/repair;
- approval/intervention mechanisms;
- diffs, traces, artifacts, and persisted evidence;
- Run Console inspection;
- Studio Chat with bounded workspace/Mission/run diagnostic context;
- Windows packaging/release infrastructure.

## Immediate gap
First-class GitHub delivery is not yet a complete polished loop. Local Git/worktree execution exists, and publishing-shaped commands are treated as high risk, but Agentic Studio still needs first-class GitHub connectivity for issue/repository intake and delivery/CI feedback.

## Next target: self-hosting preview
Acceptance path:

GitHub issue/objective
→ Agentic Studio Mission
→ isolated worktree
→ agent implementation
→ build/tests
→ bounded repair
→ human review/publishing approval
→ commit/push
→ create/update PR
→ observe GitHub Actions
→ repair CI failures when permitted
→ present green PR for Connor verification/merge

A strong next release name is Alpha 0.3 — Self-Hosting Preview, but release naming can change if repository planning says otherwise.

## Near-term success criterion
Connor should be able to give Agentic Studio an Agentic Studio issue and remain inside Agentic Studio while the system develops the change through a review-ready GitHub PR without manually relaying implementation prompts through an external chat.
