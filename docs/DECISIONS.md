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
| Explore bringing the game to a modern World of Warcraft client | Explicit direction, 2026-11-01 | **Intended**, feasibility not yet assessed |

The creative decisions above are not claims that every rule is enforced perfectly by v0.72.

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

- Which modern WoW client should host the next version, and does it retain a suitable ball item and throw interaction?
- Can item receipts, map locations and close-range detection be implemented reliably in that client?
- Should the four middle checkpoints become mandatory or ordered?
- Should penalty timing, chat volume or score sharing change?
- What compromises preserve the original enjoyable game when some 1.12 assumptions no longer hold?

These are **undecided**. Investigating a modern edition does not approve any particular redesign.

## Documentation decisions

**2026-10-26:** AI-assisted reconstruction separated source behavior from historical intention without modifying gameplay.

**2026-11-01:** The creative supplied additional first-person origin details and confirmed an intention to investigate a modern-client edition. AI revised the documentation accordingly; gameplay behavior and compatibility remain untested.
