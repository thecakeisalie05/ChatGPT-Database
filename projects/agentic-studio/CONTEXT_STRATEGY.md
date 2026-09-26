# Context Strategy

This repository exists because Studio Chat does not automatically inherit unrelated ChatGPT conversation history.

Do not solve that by injecting complete chat archives into every prompt.

## Desired model
Project knowledge should eventually be maintained by a Project Brain that can retrieve relevant context from:
- repository documentation and source;
- durable product/architecture decisions;
- previous Missions and their evidence;
- current-state manifests;
- human interventions and acceptance decisions;
- research logs;
- explicitly remembered project notes.

Only the relevant bounded context should be attached to a conversation or Mission.

## Bootstrap approach
Until Project Brain provides this natively:
1. keep durable cross-chat context in this curated repository;
2. keep current source truth in the actual project repository;
3. maintain a concise CURRENT.md;
4. update durable decisions instead of appending endless transcripts;
5. archive obsolete context rather than letting contradictions accumulate.

A future Agentic Studio feature should make 'remember this for the project' explicit and inspectable.
