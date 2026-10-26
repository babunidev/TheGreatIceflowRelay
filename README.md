**Author:** Babuni.dev

The Great Iceflow Relay

Hi yall,

This is a little relay ball game add-on for World of Warcraft 1.12, played on Iceflow Lake in Dun Morogh.
It’s a simple but fun RP activity where you and your friends run through checkpoints, pass the ball around, and try to score the most Iceflow Shards while avoiding penalties.

I made this addon because I love throwing the ball in WoW, but just passing it back and forth got a little stale. So I thought, why not turn it into a proper mini-game? I’m new to addon development and not much of a coder, so I used AI help to put this together. It’s pretty simple, mostly chat commands, but I think it adds a cute bit of gameplay for anyone who enjoys RP events and silly fun with the ball.

🏁 How the game works

There are 6 checkpoints: one Start, four in between, and one Finish.

The race begins at the landing stage in Brewnall Village.

To prepare, you can:

Type /iceflow checkpoints → see coordinates of all checkpoints.

Move to a spot and type /iceflow check → see if you are standing inside a checkpoint.

🎮 Commands

/iceflow ready → Arms the addon and signals the group that you’re ready.

Enter the Start checkpoint → Relay begins and everyone gets a group message.

/iceflow end → Disarms the addon.

/iceflow pos → Prints your current coordinates.

/iceflow ballcheck → Tells you if you have a leather ball in your bags.

💎 Scoring

Players earn Iceflow Shards when:

Catching the ball.

Entering a checkpoint.

Players get penalties for:

Holding the ball too long.

Standing too close to another player (must stay at least 28 yards apart).

At the Finish checkpoint, the addon posts a summary to the group chat:

Total Shards earned.

Total Penalty collected.

Net Shards (your final score).

👥 Group Play

Designed mainly for pairs, but works fine with more players too.

Example: three players can run in a triangle, passing two or even three balls around at once.

Works in both party and raid groups.

🗺️ Route

The checkpoints can be tricky to find, so here’s a marked map of the course:
https://imgur.com/a/eQcNdPX


✨ Closing words

This addon is meant as a light RP mini-game for World of Warcraft 1.12. It’s not super polished, but it’s fun if you like silly challenges with friends.

Wishing yall lots of joy and many Iceflow Shards in Azeroth!

## Current source snapshot (v0.72)

**Scope:** The source targets a World of Warcraft 1.12 / Lua 5.0-style client. The source has **not** been retested in game for this documentation review. The rules below describe implementation, which sometimes differs from the event's idealized group-play description above.

1. Every participant who installs and arms the addon tracks their **own** run. The code does not send a synchronized scoreboard, coordinate other players' state, or enforce that every player visits the same stops.
2. Four intermediate checkpoints can each award **one shard once per run**. The current code accepts them in any order and allows the player to finish without visiting all four.
3. Receiving an item matching the **Heavy Leather Ball** icon through `ITEM_PUSH` can award **one shard**, subject to a 0.1-second duplicate-event guard.
4. If a Heavy Leather Ball is found in bags while a run is active, the current polling implementation adds **one penalty per two-second check**. It does **not** measure elapsed holding seconds precisely or provide a grace period.
5. The ~28-yard proximity test uses `CheckInteractDistance` on **your current target**, whether or not that unit is a teammate. A nearby untargeted player is not checked.
6. The finish message reports net shards, total earned shards, and accumulated penalties to party/raid chat (or locally when solo). There is no built-in ranking of multiple finishers.

### Installation and setup

Install `TheGreatIceflowRelay.lua` and `TheGreatIceflowRelay.toc` directly inside `Interface/AddOns/TheGreatIceflowRelay/`, restart your game and enable the addon. The addon's manifest declares interface `11200` and version `0.72`.

Use `/iceflow rules` to read the in-game rules and `/iceflow checkpoints` to print every checkpoint rectangle. Use `/iceflow ready` to arm the run and enter the start area. The addon then polls for checkpoints, bag contents, and proximity. `/iceflow end` stops it; `/iceflow pos`, `check`, and `ballcheck` provide diagnostics.

### Project record

The creator's first-person story above is preserved as historical testimony. The technical sections distinguish original ambitions from the implementation. The GitHub development journal documents observed iterations and admits what cannot be verified.

- [Creative concept](CONCEPT.md) · [Experience design](docs/DESIGN.md) · [Course and content](docs/CONTENT.md)
- [Architecture](docs/ARCHITECTURE.md) · [Decision record](docs/DECISIONS.md) · [Development journal](docs/DEVLOG.md)
- [Roadmap](ROADMAP.md) · [Changelog](CHANGELOG.md) · [Human–AI collaboration](docs/AI_COLLABORATION.md) · [Agent guidelines](AGENTS.md)

## Development documentation

- [Concept](CONCEPT.md) · [Roadmap](ROADMAP.md) · [Changelog](CHANGELOG.md)
- [Architecture](docs/ARCHITECTURE.md) · [Design evidence](docs/DECISIONS.md) · [Development journal](docs/DEVLOG.md)
- [AI collaborator rules](AGENTS.md)

The development journal distinguishes original author direction, source-based reconstruction, AI assistance, and independently verified behavior.
