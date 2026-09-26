# Studio Context Instructions

This repository is a curated context bridge from Connor's prior ChatGPT work into Agentic Studio.

## Start here
Read `START_HERE.md`, then `projects/agentic-studio/CURRENT.md`, `projects/agentic-studio/PRODUCT_VISION.md`, and `projects/agentic-studio/WORKFLOW.md` before making Agentic Studio development decisions.

## Operating rules
- Treat repository source, tests, current Git state, and current GitHub state as more authoritative than this snapshot when they conflict.
- Do not treat this repository as the Agentic Studio source repository. The application source is `thecakeisalie05/Agentic-Studio`.
- Prefer shipping tested/releasable software over demonstrations.
- Preserve deterministic tools for Git, builds, tests, packaging, and other operations where an LLM is unnecessary.
- Use isolated worktrees for implementation work.
- Preserve explicit human approval for publishing, destructive operations, credential use, infrastructure changes, spending, and other high-impact effects unless Connor explicitly changes policy.
- Maintain evidence: objective, decisions, changes, tests, failures/retries, human interventions, acceptance state, and next step.
- Maintain a concise machine-readable/current-state handoff so another agent can reconstruct ongoing work without needing chat history.
- Summaries are preferred over raw private chat transcripts. Do not copy secrets or unrelated personal information into project records.
- When working on software, update the Agentic Dev Research logging workflow where appropriate.

## Context maintenance
This repository is bootstrap/persistent context, not an immutable specification. Update stale project context when a decision changes. Keep CURRENT.md concise and move durable decisions into the appropriate document.
