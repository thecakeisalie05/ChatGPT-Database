# Curated Development History

## 0.1 foundation
Agentic Studio established the Electron desktop foundation, workspace/repository tooling, editor/terminal, Git/worktrees/checkpoints, Harness Canvas, deterministic Demo execution, traces, approvals, retries, artifacts, agent/skill/MCP concepts, Academy material, Codex integration, packaging, and tests.

## Mission Runtime push
The 0.2 effort shifted from a demo harness toward durable Missions: versioned Mission state, typed runtime packets, generic DAG scheduling, provider-neutral execution, live Codex/OpenAI nodes, managed worktrees, deterministic validation, bounded repair, intervention, persistent evidence, and recovery.

The design deliberately avoided making Project Brain, multiple additional providers, analytics, passive development, portfolio scheduling, or broad release automation blockers for the first dogfood path.

## D0 preparation
The D0 runbook established the desired real path:
Mission → isolated worktree → live implementation → deterministic validation → repair/evidence → human inspection/intervention → diff review → durable trace.

Issue #10 was designated as an early real self-hosting task.

## Studio Chat
Studio Chat was added as a first-class ChatGPT-labelled collaboration surface with persisted threads/streaming and bounded live diagnostic context for workspace, Mission, run, events, and runtime readiness.

Installed Alpha 0.2 initially exposed practical blockers including Windows discoverability and chat response/runtime problems. Hotfix work added Start-menu shortcut handling, response buffering, consolidated the assistant UX, and updated the bundled Codex runtime for Astra compatibility.

By 2026-09-26, Connor verified Alpha.2 installed successfully, appeared in Windows search, and Studio Chat worked end-to-end.

## Current transition
Development is now intentionally moving toward using Agentic Studio to develop Agentic Studio. The remaining major near-term gap is first-class GitHub intake/delivery/CI integration.
