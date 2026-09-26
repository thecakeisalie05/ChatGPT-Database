# Architecture Context

## Canonical conceptual objects
- Mission: durable human objective plus executable workflow/state.
- Harness/runtime graph: orchestration structure through which work executes.
- Agent/provider node: model-backed worker behind a normalized boundary.
- Typed packet/context capsule: bounded structured information passed between stages.
- Worktree: isolated Git working directory for implementation.
- Approval/intervention: explicit human control boundary.
- Trace/evidence/artifact: durable explanation and output of execution.
- Project Brain: future persistent project knowledge/context retrieval layer.

## Responsibility boundaries
Electron main process owns privileged operations such as filesystem, SQLite, Git/worktrees, processes, MCP, secrets, and providers. Renderer owns presentation/graph/editor state. Shared code owns serializable typed contracts. IPC should be typed, allowlisted, and validated; avoid generic arbitrary-command bridges.

## Execution direction
Mission execution should be provider-neutral. Deterministic Demo behavior remains valuable for tests/demos. Live Codex/OpenAI execution should use the same normalized runtime/evidence surfaces where possible.

## GitHub architecture direction
Do not make an LLM emulate GitHub when deterministic integration is available.

Preferred split:
- local Git handles status, diff, worktrees, commits, and repository operations;
- a first-class GitHub connection handles repository discovery, issues, PRs, CI/checks, comments, and releases;
- Mission policy controls which remote effects require approval;
- GitHub is durable software/release state, not Agentic Studio's orchestrator.

The first-class GitHub layer should ultimately make issue → Mission → PR → CI feedback a native loop.
