# Development Workflow and Human/Agent Contract

## Connor's role
Connor supplies product intent, priorities, constraints, architecture direction, subjective QA, intervention/corrections, and final acceptance/rejection. The workflow should preserve these contributions explicitly rather than reducing authorship to lines of generated code.

## Agent role
Agents may plan, inspect, implement, build, test, diagnose, retry, prepare changes, and produce evidence within granted permissions. Agents should surface uncertainty and blockers rather than silently broadening scope.

## Preferred execution path
1. Capture objective and acceptance criteria.
2. Resolve relevant project context.
3. Create an isolated implementation worktree.
4. Implement the smallest coherent change.
5. Run deterministic validation.
6. On failure, preserve evidence and perform bounded repair.
7. Expose diff, tests, trace, decisions, and artifacts.
8. Allow human inspection/intervention.
9. Require policy-appropriate approval for external effects.
10. Deliver through Git/GitHub.
11. Record final acceptance and research evidence.

## Publishing boundaries
Default posture:
- read repository/status/issues: low risk;
- edit isolated worktree: allowed according to Mission policy;
- builds/tests: automatic where safe;
- local commit: configurable;
- push / PR creation or update: explicit approval initially;
- merge / release: explicit human approval;
- destructive actions, credential use, infrastructure modification, or spending: explicit approval.

These may become configurable after dogfooding proves the safety model, but never silently relax policy.

## Current-state manifests
Every active agent/task/sub-thread should maintain enough machine-readable current state for another process to reconstruct:
- objective and acceptance criteria;
- current step/status;
- important context;
- changes/discoveries;
- decisions;
- touched artifacts/files;
- tests and outcomes;
- blockers;
- next action;
- links/pointers to deeper evidence.

This is essential for parallelism, interruption recovery, remote supervision, and handoffs.

## Research logging
When specifically working on a software/programming project, maintain the Agentic Dev Research workflow. Capture task/project, model/agent when known, attempts, build/test/CI outcomes, runtime failures, human interventions/corrections, subjective QA, acceptance state, and evidence.

Prefer summaries and objective evidence over full transcripts. Maintain a human-readable/public-facing layer explaining what Connor did, what agents did, what failed, what mattered, and what the workflow enabled.
