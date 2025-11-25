# **CMDF_EXECUTION_SPEC.md**

### *Internal Execution Guide for ChatGPT – Connor Memory Delta Filter (CMDF)*

### *Version: 2.0 — Fully Integrated*

> **Purpose:**
> This document defines the exact procedure ChatGPT must follow to execute CMDF—Connor’s Memory Delta Filter—accurately, deterministically, and consistently across all future runs.

This specification overrides improvisation and enforces strict rules for:

* parsing conversations
* generating deltas
* applying filters
* determining knowledge confidence
* producing CMDF-SOF output
* handling commands
* avoiding false positives
* and excluding meta commands

---

# 1. **Top-Level Rule**

CMDF execution must always follow:

```
TOKENIZE → STABILITY FILTER → DIFFERENTIAL FILTER → NOISE FILTER → SENSITIVITY FILTER → NORMALIZE → DELTA BUILD → SOF OUTPUT
```

No step may be skipped, reordered, or replaced.

---

# 2. **Conversation Input Resolution**

CMDF runs on a *conversation target*, provided by the user via `CMDF [args] [target]`.

Target resolution:

1. If a URL is provided → treat as conversation link.
2. If a text block is provided → use text block literally.
3. If a descriptive phrase is provided → interpret as historical chat pointer.
4. If omitted → use **current conversation only**.

---

# 3. **CMDF-FULL-SCAN-MODULE (Mandatory)**

### ChatGPT must:

* Scan **every message** of the conversation target.
* Process messages **in chronological order**.
* Tokenize **each message independently**.
* Maintain message boundaries (no merging).
* Apply filters **per token, per message**, before combining.
* Guarantee **no skipped content**.

This prevents partial or biased deltas.

---

# 4. **Tokenization Rules**

Every message is decomposed into **event tokens** from the following classes:

```
SKILL
DEVICE
PROJECT
CODE_STYLE
COGNITIVE_PATTERN
BEHAVIOR_ROUTINE
PREFERENCE
HARDWARE_STATE
SOFTWARE_STATE
GAMING_STATE
LONG_TERM_GOAL
EMOTIONAL_PATTERN
COMMUNICATION_STYLE
REASONING_STYLE
CREATIVE_DOMAIN
PREFERENCE_DETAIL
KNOWLEDGE_CONFIDENCE
META_INFO
REDUNDANT
EPHEMERAL
SENSITIVE
```

**Tokenization must be exhaustive** — any meaningful piece of information becomes a token.

---

# 5. **CMDF-EXCLUSION-MODULE**

If a message:

* begins with `CMDF`
* contains any CMDF flags (`-v`, `-d`, `-c`)
* or is a procedural memory instruction

→ **It MUST be excluded from tokenization**.

These messages are control-flow, not content.

---

# 6. **S-FILTER (Stability Filter)**

A token is *kept* only if it represents a **stable, multi-session, long-term pattern**, such as:

* a recurring skill
* a persistent technical domain
* a long-term project
* a stable preference
* an ongoing behavioral/cognitive pattern
* a durable emotional style
* real hardware or software actually owned
* creative/technical domains sustained over time
* new knowledge with recurring evidence

Tokens representing one-off events or fleeting states must be dropped.

---

# 7. **Knowledge Confidence Modeling**

CMDF must **not** assume knowledge or mastery from interest alone.

For every knowledge-related token, ChatGPT must assign one of:

* `low`
* `medium`
* `high`

Determined by:

* repetition across messages
* demonstrated application
* debugging skill
* high-level reasoning
* historical consistency

Confidence is stored as a `KNOWLEDGE_CONFIDENCE` token tied to the skill domain.

---

# 8. **D-FILTER (Differential Filter)**

A token passes to the delta only if:

1. It **does not match** existing memory (semantic similarity < 0.75) → `DELTA_NEW`
2. It **extends** existing memory (new detail, refinement, or updated confidence) → `DELTA_APPEND`

All other tokens must be discarded.

---

# 9. **N-FILTER (Noise Filter)**

These tokens MUST be dropped:

* One-off complaints or states (“I’m tired”)
* Temporary actions
* Short-lived emotional reactions
* Debug instructions not representing sustained behavior
* One-use technical commands
* Anything not likely to persist

---

# 10. **SEC (Sensitivity Filter)**

Unless user explicitly requests storage, discard tokens describing:

* exact addresses
* passwords
* credentials
* banking details
* medical diagnoses (except explicitly permitted ones like OCD)
* location-specific data

Always err on the side of dropping sensitive content.

---

# 11. **Normalization**

Every surviving token must be converted into canonical form.

Example:

### Raw:

> “I use a GTX 1080 in my desktop.”

### Normalized:

```json
{
  "category": "DEVICE",
  "value": { "type": "gpu", "model": "GTX 1080" },
  "confidence": "high"
}
```

Normalization rules must be:

* lossless
* domain-specific
* structured
* deterministic

---

# 12. **Delta Construction**

Final delta MUST be structured into:

```
delta.new
delta.append
```

Each containing the following guaranteed category keys:

```
skills
devices
projects
code_style
cognitive
emotional
communication
reasoning
creative
preferences
hardware_state
software_state
gaming_state
automotive
meta_info
```

Even if empty.

---

# 13. **CMDF-SOF 1.0 (Mandatory Output Format)**

All CMDF runs must output:

```
CMDF_OUTPUT {
  metadata:{ ... },
  verbose_trace:{ ... },
  delta:{ new:{...}, append:{...} },
  normalized_tokens:{ tokens:[...] }
}
```

### Rules:

* All sections must always be present.
* Even empty lists must appear.
* JSON-like structure; deterministic keys; stable ordering.
* No omissions allowed.

---

# 14. **CMDF-CLI Command Handling**

ChatGPT must interpret:

```
CMDF [arguments] [conversation_target]
```

Flags:

* `-v` → verbose
* `-d` → dry-run (debug)
* `-c <category>` → category restriction

### Execution flow:

1. Parse flags.
2. Resolve conversation target.
3. Apply CMDF-FULL-SCAN.
4. Apply all filters.
5. Apply category filter (if present).
6. Produce SOF output.
7. If not in debug mode:

   * Ask user for approval before committing to memory.

---

# 15. **Error Handling Rules**

Errors must be included in:

```
metadata.status = "error"
```

Common errors:

* missing conversation content
* invalid category
* malformed command
* insufficient data for tokenization

---

# 16. **Strict Determinism**

Given identical input + memory state, CMDF must produce **identical output**.

This is guaranteed by:

* deterministic token ordering
* deterministic filter ordering
* deterministic normalization
* deterministic output formatting

---

# 17. **Profile Update Protocol**

If user approves delta:

1. Integrate new/append values into memory
2. Update knowledge confidence if present
3. Prevent duplication
4. Maintain chronological consistency
5. Never overwrite explicit user-stated core identity without consent

---

# 18. **Forbidden Behaviors**

ChatGPT MUST NOT:

* improvise new categories
* invent knowledge the user didn’t demonstrate
* store sensitive info without explicit permission
* skip SOF output fields
* skip messages in conversation
* alter chronology
* store ephemeral states
* treat CMDF commands as content

---

# 19. **Testing Shortcut Commands**

User may optionally issue:

* `CMDF -selftest`
* `CMDF -dryrun current`
* `CMDF -validate`

These produce diagnostic CMDF-SOF output.

---

# 20. **Version and Extensibility**

This spec defines:

```
CMDF_EXECUTION_SPEC_VERSION = "2.0"
```

Future updates may revise:

* token classes
* filter heuristics
* knowledge rules
* CLI commands
* SOF schema

But must maintain backward compatibility unless user explicitly requests a major version upgrade.

---

# **END OF SPEC**
