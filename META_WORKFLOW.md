# META WORKFLOW

## Purpose
This repo stores the reusable control-room logic for managing multiple Codex project lanes without rebuilding the workflow from scratch in every new chat thread.

## Active lane roles
- **bee**: Bedrock bee companion logic/system project
- **statue**: Optimus staged build / reference-driven artifact project
- **coaster**: flagship gameplay/system add-on project
- **meta/control room**: workflow, routing, state tracking, upgrades, and handoffs

## Core model
- **local linked repo workspace** = Codex workspace anchor
- **AGENTS.md** = repo-specific operating rules
- **GitHub repo files** = shared memory / source of truth
- **Minecraft** = truth test for actual in-game behavior
- **meta thread** = control room, not implementation lane

## Lane separation rules
- Bee thread: bee only
- Statue thread: statue only
- Coaster thread: coaster only
- Meta thread: workflow and routing only
- Do not blur project logic between lanes

## Status header format
Use this exact compact format at the end of replies:

```text
**status**
**bee**: ...
**statue**: ...
**coaster**: ...
```

Keep status short and action-oriented.

## Handoff format
When bringing state back into control room, include only:
- the last prompt sent to Codex
- Codex's latest reply
- blocker or observed result

Do not dump entire thread history unless a specific diagnostic reason exists.

## Codex workspace rules
When a repo is cloned locally, use the local linked path as the default workspace anchor.
Reassert only if Codex loses context:

```text
Workspace root is:
D:\Jeebs mods\<repo>

Read and follow AGENTS.md there.
```

Do not spam GitHub tag/context every prompt once local linked workspace is stable.

## Repo truth rules
- Store reusable workflow logic here, not full chat transcripts
- Store stable project rules in the relevant project repo
- Store current task state in project docs such as:
  - CURRENT_SPEC.md
  - DECISIONS.md
  - NEXT_TASK.md
  - TEST_CHECKLIST.md

## Reasoning defaults
- **bee**: medium
- **statue**: medium
- **coaster**: high

Only change reasoning level when the task clearly becomes more structurally complex.

## Upgrade triggers
A workflow upgrade should be considered when any of the following happen:
1. The same instruction must be repeated multiple times
2. Codex repeatedly returns content instead of writing files
3. The user is forced into repeated receptionist-style relaying
4. A repo/local workspace/automation option becomes available that reduces manual relay work
5. A lane becomes too test-heavy and needs larger bundled debug passes

## Current operational principles
- Prefer real file writes over pasted content
- Prefer bigger coherent passes over tiny poke-test loops
- Prefer repo docs as shared memory over re-explaining rules in chat
- Treat fake progress as failure
- Keep status easy to scan for interruption-heavy real life

## Statue-specific reference logic
- `optimus_bedrock.mcfunction` = front-read / proportions / landmarks
- `optimus_17.mcfunction` = rough scaffold, not literal final depth truth
- generated lower torso refs = provisional only
- clean Optimus image refs = style cue
- if scaffold conflicts with stronger refs, reinterpret locally

## Bee-specific logic
- current goal is stable tame + alive, normal bee behavior
- do not add follow logic or feature creep until baseline behavior is stable

## Coaster-specific logic
- current goal is proof of concept first, not full product
- choose one viable Bedrock-friendly approach and prove it in game
- add quickstart/help if the POC is not self-explaining

## Fresh-thread reboot rule
When the meta thread becomes bloated, start a new one and use this repo/doc as the baseline instead of rebuilding the workflow from memory.
