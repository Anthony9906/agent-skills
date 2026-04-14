---
name: memory-lite
description: Use a lightweight long-term memory workflow based on Obsidian, with truth, state, rules, and sources kept separate and updated with low friction.
---

# Memory Lite

Use this skill to operate the workspace's long-term memory in a lightweight, low-friction way.

## Core idea

Do not build a heavy memory bureaucracy.

The goal is simple:
- preserve truth
- preserve current state
- preserve rules
- preserve sources
- update memory when it clearly helps future continuity

## Primary memory vault

Treat this Obsidian vault as the primary long-term memory:
- `${WORKSPACE_ROOT}/Obsidian-Agent-Memory`

## Core memory surfaces

When memory is needed, prefer these core notes first:
1. `00 Home/Memory Hub.md`
2. `03 Facts/Core Facts.md` -> truth
3. `01 Working/Active Context.md` -> current state
4. `02 Procedural/Collaboration Rules.md` -> rules
5. `04 Sources/Source Index.md` -> sources

Do not read the whole vault by default. Start from the core notes and expand only when needed.

## Two-layer structure

Treat the memory system as two layers:
- Core layer: fast context recovery
- Extended layer: detailed notes, history, and traceability

The core layer is:
- `00 Home/Memory Hub.md`
- `03 Facts/Core Facts.md`
- `01 Working/Active Context.md`
- `02 Procedural/Collaboration Rules.md`
- `04 Sources/Source Index.md`

The extended layer includes:
- `01 Working/`
- `02 Procedural/`
- focused notes in `03 Facts/`
- source notes in `04 Sources/`
- `05 Feedback/`
- `06 Sessions/`

## Memory object model

Use these practical categories:
- Truth: stable, confirmed facts
- State: what is currently active, changing, blocked, or next
- Rules: reusable working rules, preferences, collaboration conventions
- Sources: where a fact, request, or decision came from
- Sessions: optional support material when a substantial conversation should be preserved

## Retrieval rule

Only consult more memory when there is a clear reason, such as:
- the user signals continuity (`继续`, `上次`, `之前`, `那个项目`)
- the user references an established topic, project, file, or decision
- the response depends on prior preferences or working rules
- the user asks for rationale, prior decisions, constraints, or evidence

Otherwise, avoid unnecessary memory lookup.

## Update rule

At the end of a substantial conversation, check whether memory should be updated.

A substantial conversation usually means one of these happened:
- a new stable fact was confirmed
- the current state changed
- a new rule or preference was established
- an important new source appeared
- a meaningful decision was made

If none of these happened, do not force a memory update.

## Writing rule

Prefer updating existing notes over creating many new notes.

Use this default mapping:
- stable fact -> update `Core Facts.md` or a focused fact note
- current status / next step -> update `Active Context.md`
- collaboration preference / reusable rule -> update `Collaboration Rules.md` or `Collaboration Feedback.md`
- evidence / original request / external reference -> update `Source Index.md` and add a source note when needed

Additional writing rules:
- keep core notes short and scannable
- put details into focused notes and keep summaries plus links in core notes
- prefer replacing stale state over appending more state
- remove or migrate invalidated state out of core notes

## Session rule

Do not create a session note by default.

Create one only when at least one of these is true:
- an important decision was made
- an important new source appeared
- a meaningful stage transition happened
- future traceability is likely to matter

## Separation rule

Always keep these separate:
- truth
- current state
- rules / preferences
- sources / evidence

Do not mix evidence with conclusions if it can be avoided.

## Simplicity rule

Avoid creating:
- large review queues
- heavy ledgers
- overly detailed state machines
- too many tiny notes unless they clearly improve reuse

The system should remain readable, maintainable, and easy to keep updated.

## Maintenance actions

Default to only these lightweight actions:
- append: add a new stable item worth keeping
- replace: update an existing item with newer truth or state
- archive/remove: move stale state out of the core layer

## Ambiguity rule

If a possible memory update is ambiguous or may misrepresent the user, ask briefly or keep it out of long-term memory.

## Output habit

When relevant, end substantial conversations with brief suggested or executed memory updates.
