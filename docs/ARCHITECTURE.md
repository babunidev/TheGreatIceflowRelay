# The Great Iceflow Relay — architecture

**Source version:** 0.72 · Interface 11200 · World of Warcraft 1.12 / Lua 5.0-style client  
**Evidence:** `TheGreatIceflowRelay.lua` and `TheGreatIceflowRelay.toc` inspected on 2026-11-01. This is static analysis, **not an in-game test**.

## Runtime overview

The addon consists of one Lua file and a TOC manifest. It creates `TheGreatIceflowRelayFrame`, registers `ITEM_PUSH`, attaches `OnEvent` and `OnUpdate`, and registers `/iceflow` commands. The frame begins hidden.

The `ready` command resets local counters, sets `armed = true` and shows the frame. Crossing the start rectangle while armed sets `runActive = true`. The update handler runs when armed or active and, after approximately `CHECK_INTERVAL = 2` seconds, performs three checks.

| Check | Mechanism | Outcome |
| --- | --- | --- |
| `CheckCheckpoint` | Sets current map, reads normalized `GetPlayerMapPosition("player")` and checks `GetZoneText() == "Dun Morogh"` | Starts run, grants first-visit checkpoint shards or finishes run |
| `CheckBallInInventory(true)` | Scans bag links for the literal English `Heavy Leather Ball` | When active and found, adds 1 penalty on that polling pass |
| `CheckTargetDistance` | Calls `CheckInteractDistance("target", 1..4)` on the selected target | Adds 1 penalty on a positive close-distance result; no group scan |

Separately, the `ITEM_PUSH` event handler inspects the second event argument for `INV_Misc_ThrowingBall_01`. When the run is active and the event is outside a 0.1-second duplicate guard, it adds **1 shard**. It does not validate the sender or complete ball-transfer semantics.

## State and scoring

- Run flags: `armed`, `runActive`, `startTriggered`, `finishTriggered`.
- Rewards: `playerShards`, `visitedCheckpoints` (once for each middle landmark).
- Penalties: `totalPenalty`; `totalBallTime` is incremented per **poll**, not per elapsed second despite older wording.
- Timing and inventory: `hasBall`, `lastCheck`, `lastBallCatch`.
- Finish: `netShards = playerShards - totalPenalty`, announced to the group or printed locally.

There are no declared saved variables, addon communication messages, network-shared score tables or standings. A reload resets runtime state.

## Multiplayer and lifecycle boundaries

`RelayGroupMessage` sends to **RAID** when raiding, otherwise **PARTY** when grouped, otherwise local chat. `RelayLocalMessage` prints locally. Each client independently decides when its own run starts, gains points and finishes.

After finishing, `runActive` becomes false, while `armed` remains true; re-entering the start can initiate another run. `/iceflow end` disarms, stops scoring and hides the frame.

## Known discrepancies and potential failure points

- The middle checkpoints have no enforced order, and reaching all four is not required to finish.
- The distance test applies to the **current target**, which may be an NPC or other non-teammate.
- Bag holding incurs penalties per polling tick; `ballcheck`'s “sec” output is therefore misleading.
- `/iceflow check` tests coordinate rectangles without the normal automatic zone guard.
- Map rectangles are **not** yard-distance areas. Brief crossings can fall between polling passes.
- Item name, icon, zone text, map APIs and legacy events require real client validation.
- Existing 1.12 interfaces say nothing by themselves about modern WoW API compatibility.

## Modern-client investigation

Before porting, verify the exact target build, throwable item behavior, modern bag/inventory event and map APIs, protected operations, communication restrictions and any ability to evaluate teammate distance. Reproducing the original **social game** may be possible even if individual technical shortcuts must change. No modern implementation or test is recorded yet.
