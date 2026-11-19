# The Great Iceflow Relay — decisions

**Creative:** Babuni  
**Purpose:** Separate the creative's confirmed choices from implementation observations and unresolved proposals.

## Established creative direction

| Decision | Basis | Status |
| --- | --- | --- |
| Make a game from the existing WoW ball-throwing interaction | First-person account of playing catch with my brother, running and jumping while passing | Established creative origin |
| Build rules around a ball that cannot be stopped in flight | Creative's explanation of the game's limits | Established design principle |
| Keep the full name **The Great Iceflow Relay** | Explicit naming choice, reaffirmed 2026-10-31 | Confirmed |
| Use the Iceflow Lake / Brewnall Village gnomish setting | Original course and current creative account | Established setting |
| Reward movement and catches while penalizing holding and proximity | Original game rules; current scoring source | Established concept |
| Explore bringing the game to a modern World of Warcraft client | Explicit direction, 2026-11-01 | Direction set. The client was named on 2026-11-19. See the Forever rows. |
| Host the next edition on **WoW Forever**, in files separate from the preserved 1.12 addon | Named as the target on 2026-11-19 | **Intended.** The port is not built. A live client has not been surveyed. |
| Keep the rectangular scoring zones, and show where they are | Checkpoints were hard to find during play; visible guidance was requested on 2026-11-19 | **Intended** gameplay change. Map pins and one tracked waypoint. Not implemented. |
| Treat world flares as a hand-placed group mark | Public API notes: a flare is placed by clicking the ground, and an addon cannot read its position back | Recorded with the guidance decision. Flares sit beside the rectangles. They do not award shards. |

The creative decisions above are not claims that every rule is enforced perfectly by v0.72. Public API notes are not a playtest.

## Implemented technical approaches

| Feature | Source evidence | Qualification |
| --- | --- | --- |
| Six rectangular course zones | `checkpoints`, `CheckCheckpoint` | Earlier prototype used triangles |
| Armed start and local run state | `/iceflow ready`, `StartRun` | No cross-client start synchronization |
| Once-per-stop checkpoint shards | `visitedCheckpoints` | No forced order or requirement to complete all middle stops |
| Catch shard | `OnItemPush` | Matching event/icon, not proof of a complete player-to-player exchange |
| Carrying penalty | `CheckBallInInventory` | One penalty per ~2-second check with ball in inventory |
| Spacing penalty | `CheckTargetDistance` | Checks only current target; target need not be a teammate |
| Party/raid announcements | `RelayGroupMessage` | No synchronized shared scoreboard |

Implementation demonstrates what the code does, not who first suggested every function or an unrecorded design approval.

## Historical iteration

On **11 September 2025**, the earliest checkpoint geometry was triangular; subsequent commits changed the structure to rectangular regions and separate start/finish areas. Later commits added event-based catching, revised penalties and improved group announcements. Those changes are recorded in [the development journal](DEVLOG.md). The original discussion behind each technical change has not been recovered.

## Questions still open

- The live Forever survey is still open: exact build, TOC suffix, whether the v0.72 rectangles still match, a real ball throw, distance yards, party map links, and flare permissions. Public item pages describe item 18662 as throwable. That description has not been tried in a client.
- Should the four middle checkpoints become mandatory or ordered? The intended guide points at the nearest remaining stop, and a different order still counts.
- Should penalty timing, the “Distance ok!” line, or score sharing change?
- What further compromises preserve the original game when a live client disagrees with the public API notes?

These are **undecided**. Choosing Forever, and choosing to show the rectangles, does not approve a required route, new penalty timing, a scan of every teammate, or a shared scoreboard. The feasibility detail is in [FOREVER.md](FOREVER.md).

## Documentation decisions

**2026-10-26:** AI-assisted reconstruction separated source behavior from historical intention without modifying gameplay.

**2026-11-01:** The creative supplied additional first-person origin details and confirmed an intention to investigate a modern-client edition. AI revised the documentation accordingly; gameplay behavior and compatibility remain untested.

**2026-11-19:** WoW Forever was named as the intended client, and visible guidance on top of the existing rectangles was accepted as the gameplay change for that edition. Cursor (Grok 4.7) researched public APIs and drafted the roadmap and feasibility note. No Lua or TOC file changed, and no client was tested.
