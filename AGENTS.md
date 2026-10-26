# The Great Iceflow Relay — AI/developer collaboration rules

**Creative author and project owner: Babuni.dev.**

The project is a playful **in-world WoW ball-passing relay**. Its purpose, course, Iceflow Shards, social rules and first-person history belong to the creator. Never present this as a generic racing addon or claim AI conceived the experience.

## Before any implementation

1. Read the creator's original story in `README.md`, then `CONCEPT.md`, `docs/DESIGN.md`, `docs/DECISIONS.md`, `docs/ARCHITECTURE.md` and the current Lua/TOC.
2. Preserve the creator's voice. Keep source-based reconstructions distinct from first-person testimony and actual dated commits.
3. Mark all AI suggestions as **proposed** until the creator explicitly accepts them; do not quietly convert open design questions into requirements.
4. Treat live game behaviors as unverified until actually tested in a compatible World of Warcraft client. Cite test context, steps and results rather than writing “works” from static inspection.
5. Retain all existing creator/third-party credits and the license; never publish private conversations, credentials or unapproved chat logs.

## Implementation constraints

- Target WoW interface 11200 and Lua 5.0 conventions unless directed otherwise.
- Current source is a **single Lua file**, polled approximately every two seconds, with no persisted or network-shared game state.
- Inspect risks from map-coordinate APIs, item/icon localization, `ITEM_PUSH` payloads, `CheckInteractDistance`, group messaging and OnUpdate callbacks before touching rules.
- Clarify whether proposed fairness fixes would change the creator's intended casual RP experience.
- Update README, CHANGELOG, DEVLOG, DECISIONS, ARCHITECTURE, DESIGN and the test backlog alongside runtime changes. Include exact commit references and verified/unverified outcomes.

## Documentation-specific requirement

Keep a clear distinction between **user direction**, **AI contribution**, **iteration**, **decision**, **actual change**, and **verification**. A source snapshot proves implementation, not who originally proposed a mechanic.
