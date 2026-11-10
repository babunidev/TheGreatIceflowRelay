# The Great Iceflow Relay

A gnomish ball game on Iceflow Lake in Dun Morogh. Players run between landmarks, pass the ball and collect Iceflow Shards to score.

**Creative:** Babuni  
**Original addon:** v0.72 · World of Warcraft 1.12 · Lua 5.0  
**Status:** The original game is preserved. A modern-client adaptation is planned, and feasibility still needs assessment.

## How it began

Throwing a ball back and forth with my brother was one of those small pleasures in World of Warcraft that never really needed a purpose. We would run around, jump, change direction, and throw it again. That was fun on its own, but eventually a question took hold: could this simple item become an actual ball game?

The limitations made the question interesting. Once the ball was thrown, there was no way to stop it in flight or turn it into a conventional game of blocking and intercepting. It lived in our inventories and travelled through the game's existing throw interaction. Rather than trying to reproduce a sport that the game could not support, I wanted rules that made sense *because* of those limitations.

That became **The Great Iceflow Relay**, a little gnomish competition on Iceflow Lake outside Brewnall Village in Dun Morogh. Players move between landmarks, throw the ball, collect Iceflow Shards, and try to finish with the best score. The idea became something of an obsession: seeing whether these simple mechanics could really support a game was part of the fun. With AI assistance on the Lua implementation, the original version became playable, and playing it proved enjoyable.

The original game remains a personal example of making something new from the few interactions a game already provides.

## How to play

Gather at the starting stage near **Brewnall Village**, ideally as a pair or small group, with one or more **Heavy Leather Balls**. Each player who wants automatic scoring installs and arms the addon.

1. Type `/iceflow ready`, then enter the **Starting Stage** to begin your own run.
2. Travel around Iceflow Lake and pass the ball to one another while moving.
3. Reach the four intermediate landmarks to earn **1 Iceflow Shard** at each, once per run.
4. Receive a ball during an active run to earn **1 additional shard**, when the addon recognizes the item-receipt event.
5. Avoid penalties for carrying a ball during a scoring check or standing too close to a targeted unit.
6. Enter the **Finish Stage** at Brewnall Village. The addon announces your final score.

**Final score = shards earned − penalties.** A negative result is possible.

### Course

| Stage | Landmark | Role |
| --- | --- | --- |
| Start | Brewnall Village – Starting Stage | Begins the armed run |
| 1 | The Tree | +1 shard |
| 2 | Carcass Island | +1 shard |
| 3 | Wet Log | +1 shard |
| 4 | Behind the Branch | +1 shard |
| Finish | Brewnall Village – Finish Stage | Announces final score |

The course can be found with [the original marked map](https://imgur.com/a/eQcNdPX) or `/iceflow checkpoints`. Exact coordinate rectangles are recorded in [the course reference](docs/CONTENT.md).

### The rules and the code are not quite the same

The intended social rule is to keep moving, pass quickly, and stay roughly **28 yards apart**. The v0.72 source has more limited checks:

- **Catch:** an `ITEM_PUSH` event with the matching throwing-ball icon grants 1 shard, guarded against near-duplicate events. It does not verify the full transfer between two players.
- **Holding penalty:** when the ball is found in your bags, the active run incurs **1 penalty per check**, approximately every **2 seconds**. This is not a precise second-by-second timer.
- **Distance penalty:** each check can add **1 penalty** when your **current target** is within the interaction-distance thresholds. The addon does not track every teammate's position, and the target need not be a teammate.
- **Checkpoints:** intermediate stops can be reached in **any order**; the code does not require all four before finishing.
- **Group scores:** each player is scored **locally**. Party or raid messages share announcements, but there is no synchronized leaderboard or automatic winner selection.

These distinctions describe the current source, not a change to the original spirit of the game. Players can agree on their own event etiquette or use a referee.

## Commands

| Command | Function |
| --- | --- |
| `/iceflow rules` | Print the brief in-game rules |
| `/iceflow ready` | Arm the relay and announce readiness |
| `/iceflow end` | Disarm and stop |
| `/iceflow checkpoints` | Print every checkpoint rectangle |
| `/iceflow check` | Check whether you are inside a checkpoint |
| `/iceflow pos` | Print your map position |
| `/iceflow ballcheck` | Check whether the ball is in your bags |

## Installation

For a compatible **World of Warcraft 1.12** client, place both `TheGreatIceflowRelay.toc` and `TheGreatIceflowRelay.lua` inside `Interface/AddOns/TheGreatIceflowRelay/`. Enable the addon and use `/iceflow rules` for its in-game instructions.

The manifest declares interface **11200** and version **0.72**. This repository's current snapshot has **not** been retested in a game client during the 2026 documentation reviews. Historical play experience is not a substitute for present-day compatibility testing.

## A future on modern WoW

Bringing this game to a modern World of Warcraft client is an explicit creative goal. Whether the original ball interaction, usable item events, location APIs, and scoring behavior can be reproduced remains to be investigated. The first step is feasibility research, not an assumption that the old Lua file will run unchanged.

## Documentation

- [Concept and origins](CONCEPT.md) · [Gameplay design](docs/DESIGN.md) · [Course and commands](docs/CONTENT.md)
- [Technical architecture](docs/ARCHITECTURE.md) · [Roadmap](ROADMAP.md) · [Decisions](docs/DECISIONS.md)
- [Development journal](docs/DEVLOG.md) · [Changelog](CHANGELOG.md) · [AI collaboration](docs/AI_COLLABORATION.md) · [Contributor guidance](AGENTS.md)

The [original 2025 README](https://github.com/babunidev/TheGreatIceflowRelay/blob/03b275d/README.md) remains available in Git history. This revision expands the story with additional first-person recollections and a clearer separation between the intended rules and implemented behavior.
