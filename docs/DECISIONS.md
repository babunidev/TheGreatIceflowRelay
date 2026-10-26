# The Great Iceflow Relay — decisions and open questions

**Creator:** Babuni.dev. This register separates what the creator actually stated, what code demonstrates, and what is still undecided.

## Creator-authored direction (direct evidence)

The original, first-person [README](../README.md) explains that passing a ball around in WoW became repetitive, inspiring a **proper mini-game** in Iceflow Lake. The author describes enjoying RP activities and small group challenges, specifically passing balls among pairs or three-player triangles. The same README explicitly says AI helped with coding because the creator was new to addon development.

**This is creator testimony**, not an AI idea inferred from an implementation.

## Implemented approaches (no inferred approval dialogue)

| Implemented approach | Code / Git evidence | Important qualification |
| --- | --- | --- |
| Use in-game landmarks as checkpoint triggers | `checkpoints`, `CheckCheckpoint` | Current boundaries are rectangles; earliest committed prototype used triangles (`5c86d98`) |
| Arm before crossing start | `/iceflow ready`, `armed` and `runActive` | Historical motivations for this split are not recorded |
| Reward catches and intermediate stops | `OnItemPush`, `visitedCheckpoints` | Catch detection is icon/event-based |
| Give penalties for ball holding | `CheckBallInInventory` | One per ~2-second poll, not measured seconds |
| Discourage closeness | `CheckTargetDistance` | Checks targeted unit, not every teammate |
| Communicate in existing party/raid channels | `RelayGroupMessage`, `6b69b48` | Messaging is not multi-client state synchronization |
| Save little beyond the play session | No SavedVariables in TOC | Current design is session-local; not proof of a rejected save system |

## Source-based iteration (documented evidence)

- The first Lua commit on **2025-09-11** used **five triangle-shaped checkpoint regions**.
- Later 2025-09-11 changes converted the course to **six rectangular regions** with separate start and finish, a local shard count and repeated checkpoint logic.
- Successive changes exposed distinct **armed** versus **running** states and added bag detection, an item-event reward and a combined penalty accounting approach.
- On **2025-09-13**, commits revised finish-message wording and added **raid** messaging alongside **party** output.

These transitions are verifiable from commit diffs; the original discussions, disagreements and rejected proposals behind them have not been recovered.

## Creator decisions still required, not assumptions

- Should the course be a strictly ordered race, or intentionally allow route freedom?
- Should holding a ball incur penalties by elapsed time, frequency of checks, or only after a threshold?
- Must “too close” mean within 28 yards of **any teammate**, and how would we detect that reliably?
- Do participants need an authoritative/shared leaderboard, or is friendly local scoring sufficient?
- Should the existing English item/zone names be generalized for localization?

The documentation review did **not** answer these on Babuni.dev's behalf.

## Review decision — 2026-10-26

The assistant documented discrepancies and historical development without editing gameplay. This is a documentation action, not evidence of user approval of future feature changes.
