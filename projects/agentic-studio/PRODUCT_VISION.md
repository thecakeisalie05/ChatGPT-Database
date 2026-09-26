# Product Vision

Agentic Studio is Connor's persistent control plane for AI-assisted software development.

Its primary goal is not to demonstrate agents. It is to accelerate the production of tested, releasable applications while keeping the work observable, controllable, reproducible, and attributable.

## North star
A human objective should be able to flow through:

intent → planning → delegation → implementation → validation → repair → human approval → delivery → evidence/research logging.

The system should eventually support multiple software projects concurrently and allow Connor to leave work running without active supervision.

## Product identity
Agentic Studio combines:
- repository/workspace environment;
- visual Mission/workflow orchestration;
- model/agent execution;
- deterministic development tools;
- worktree isolation;
- approvals and human takeover;
- traces, evidence, and debugging;
- project context/Project Brain;
- GitHub delivery;
- research logging and human-readable workflow evidence;
- eventually persistent workers, parallel Missions, remote supervision, passive backlog development, and controlled continuous releases.

It is an orchestration, education, inspection, and control layer. It is not itself a foundation model and should not replace deterministic tools with LLM calls unnecessarily.

## Core principles
1. Ship useful software over flashy demos.
2. Git/GitHub remain durable source and release state; Agentic Studio owns execution state, coordination, policy, context, and evidence.
3. Deterministic tools remain first-class for Git, builds, tests, repository analysis, packaging, and releases.
4. Human control is explicit at high-impact boundaries.
5. Work should be inspectable: intent, context, actions, changes, tests, retries, failures, decisions, and artifacts.
6. Isolation should be visible. Worktrees isolate changes but are not security sandboxes.
7. Provider architecture should avoid unnecessary lock-in.
8. Context should be bounded and attributable rather than indiscriminately dumping chat history.
9. Learning/Academy documentation should evolve with user-facing capabilities.
10. Agentic Studio should eventually be capable of developing itself.

## Long-term development leverage
Desired progression:
- one useful Mission at a time;
- self-hosting development;
- parallel autonomous Missions;
- persistent/background workers;
- remote progress/failure/approval notifications;
- passive consumption of an approved backlog;
- bounded automatic build/test/repair loops;
- nightly/daily integrated builds where appropriate;
- tester feedback intake and triage;
- controlled closed-loop improvement.

Autonomy must remain bounded by resource, retry, time/cost, permission, and approval policies.
