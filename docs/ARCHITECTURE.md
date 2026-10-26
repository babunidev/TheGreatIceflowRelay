# The Great Iceflow Relay — architecture (v0.72)

**Evidence:** `TheGreatIceflowRelay.lua`, `TheGreatIceflowRelay.toc`; source inspected 2026-10-26. **No game-client execution in this review.**

## Runtime layout

A single Lua script creates `TheGreatIceflowRelayFrame`, registers the `ITEM_PUSH` event, installs `OnEvent` and `OnUpdate` handlers, and registers the `/iceflow` command. The frame starts hidden. `/iceflow ready` resets local state, sets `armed = true`, and shows the frame. Entering the starting rectangle while armed switches to `runActive = true`.

The frame's update handler checks elapsed `GetTime()` against `CHECK_INTERVAL = 2` and calls three functions while armed or active:

1. **`CheckCheckpoint`:** `SetMapZoom(0)` and `SetMapToCurrentZone()` precede `GetPlayerMapPosition("player")`; normalized coordinates are multiplied by 100. Automatic checkpoint handling also checks `GetZoneText() == "Dun Morogh"`. Intermediate areas award +1 only on first visit in a run. Finish computes `playerShards - totalPenalty`, sends summary, and disables active run.
2. **`CheckBallInInventory(true)`:** scans bag links for the literal substring `Heavy Leather Ball`. During a run, every poll where a ball is present adds **1 to `totalBallTime` and 1 to `totalPenalty`**. Despite its name and comments, `totalBallTime` is a tick count, not measured seconds; a two-second poll makes any UI “sec” wording approximate/inaccurate.
3. **`CheckTargetDistance`:** checks current `target` with the client interaction-distance API indices 1–4, then adds 1 penalty on a positive result; if out of range, it prints “Distance ok!”. It does **not** iterate party/raid members or assert target membership.

`ITEM_PUSH` separately calls `OnItemPush`, which looks for `INV_Misc_ThrowingBall_01` in the second event argument and adds one shard when active and outside a 0.1-second duplicate-event window. This is an event/icon check; not proof that the player actually received the specific named ball under every client/localization scenario.

## State and lifecycle

- **Run:** `armed`, `runActive`, `startTriggered`, `finishTriggered`.
- **Score:** `playerShards`, `totalPenalty`, per-run table `visitedCheckpoints`.
- **Item/clock:** `hasBall`, `totalBallTime`, `lastCheck`, `lastBallCatch`.
- **Persistence:** no saved-variable declaration, network protocol or shared scoreboard is implemented. Reloading resets run state.
- **End:** `/iceflow end` hides frame/disarms; finishing sets `runActive = false`, while the frame may remain visible and `armed` still true.

## Chat and multiplayer boundary

`RelayGroupMessage` uses `RAID` if in a raid, else `PARTY`, else local chat. `RelayLocalMessage` always prints locally. All score computations happen **on the local player’s machine**. Party/raid chat displays results; it is not synchronization.

## Behavior discrepancies to test or decide

- No requirement for visiting all intermediate checkpoints or visiting them in order before finish.
- A player can re-enter the start after a finished run while still armed, potentially starting again.
- Proximity is tested only against the current target, which may be a nonplayer.
- `/iceflow check` tests coordinates without the automatic Dun Morogh zone check.
- Area boundaries use small, axis-aligned rectangles, not world-space yard radii.
- Polling may skip brief boundary crossings or ball possession between two checks.
- The interface number is **11200**; modern addon API behavior is not implied.

These are code observations and possible effects, not measured game-client failures.
