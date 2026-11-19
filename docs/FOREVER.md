# The Great Iceflow Relay — WoW Forever feasibility

**Creative:** Babuni  
**Date:** 2026-11-19  
**Status:** Public research and creative direction. The port is not built. No Forever client was loaded for this note.  
**Research:** Cursor (Grok 4.7) compared `TheGreatIceflowRelay.lua` v0.72 with published Forever API notes, item listings, and zone comparisons. The choice of client, and the wish to see the checkpoints, are mine.

## Why this note exists

The 1.12 addon is the preserved game. WoW Forever is where the next edition should live, in its own files. Finding the exact spot that awarded a shard was always the awkward part of a run, so the next edition should show those spots as well as score them.

[The roadmap](ROADMAP.md) is the sequence. This note is the evidence behind it.

## What public sources still show

Forever is described as client **1.60.1**, interface **16001**, codename **Camelot**, with a mainline-style addon API. Warcraft Wiki lists `PlaceRaidMarker`, `C_Map.SetUserWaypoint`, and `C_SuperTrack.SetSuperTrackedUserWaypoint` for Forever 1.60.1.

Published zone comparisons describe Dun Morogh, including Iceflow Lake and Brewnall Village, as the same zone record as Classic Era. That makes the six v0.72 rectangles a credible place to start a survey. It does not prove the percentages still match, because the rectangles are only a few tenths of a percent wide and the poll is about every two seconds. A short crossing can still fall between checks. UiMapID **1426** is the hypothesis to test with `C_Map.GetBestMapForUnit("player")`.

Heavy Leather Ball is item **18662**. Public Forever item pages still give the use effect: throw the ball to a friendly player, and they catch it if they have room. Listings name a Leatherworking recipe and vendors including Bombus Finespindle in Ironforge. The ball still cannot be stopped in flight. That limit is why the relay exists. None of this was purchased or thrown during this research.

## Scoring can be rewritten. The old file cannot be loaded.

v0.72 calls APIs the Forever client does not provide in that form. A separate Lua file has to replace them. The behavior to keep is the local run, not the old function names.

| v0.72 call | Forever approach from public API notes |
| --- | --- |
| `SetMapZoom`, `SetMapToCurrentZone`, `GetPlayerMapPosition` | `C_Map.GetBestMapForUnit("player")` and `C_Map.GetPlayerMapPosition(uiMapID, "player")`. Treat a missing position as “not on the course.” |
| `GetZoneText() == "Dun Morogh"` | Prefer the map ID. English zone text fails on another language. |
| Bag scan for the English name `Heavy Leather Ball` | `C_Container` and item ID **18662**. Call `C_Item.RequestLoadItemDataByID` when the client has not cached the item. |
| `ITEM_PUSH` texture path `INV_Misc_ThrowingBall_01` | Camelot’s documented payload is `(bagSlot, iconFileID)`, a number. Comparing that number with `string.find` would error. The icon can be checked with `C_Item.GetItemIconByID(18662)` after item data loads. The event starts the bag animation; the slot can still read empty until `BAG_UPDATE_DELAYED`. |
| Catch shard | Award 1 shard when an active run sees the **total count of 18662 increase**, with the existing 0.1-second duplicate guard. Buying, crafting, or looting the ball during a run can still award a shard. v0.72 already treated a matching receipt as a catch. |
| `GetNumRaidMembers`, `GetNumPartyMembers` | `IsInRaid()` and `IsInGroup()`. Party and raid `SendChatMessage` remain the announcement path. `SAY`, `YELL`, and `EMOTE` need a hardware event; this game does not use those channels. |
| `UnitExists`, `CheckInteractDistance`, map coordinates | Midnight-style secret values are described as active on Forever. Branching on a secret boolean, or comparing a secret coordinate, throws. Guard with `issecretvalue` before any test. |
| `CheckInteractDistance("target", 1..4)` | The function is still documented, with indices 1–5. v0.72 treats any true result among 1–4 as too close. The yard distances, historically about 28 yards for inspect and follow, are **not verified on Forever**. |

## How the course can be shown

Three marker systems appear in the public API. They do different jobs. The rectangles remain the scoring zones. An early September 2025 experiment used triangles; v0.72 replaced that geometry with rectangles. The green world flare is a triangle symbol, which is a different thing.

### Personal guide

This is the fix for not knowing where to stand. Each player who has the addon can get:

- A pin on the Dun Morogh map and minimap for every checkpoint. Visited pins dim.
- One official user waypoint, super-tracked, so the game’s own arrow points at it. Before the run, that pin is the start. During the run it moves to the nearest middle stop not yet collected, then to the finish. Any order still scores.

The game allows one user waypoint. The other stops stay as addon-drawn pins. `C_Map.SetUserWaypoint` and `C_SuperTrack.SetSuperTrackedUserWaypoint` are both listed for Forever 1.60.1. Whether the tracked pin is also visible as an in-world mark has to be seen on a live client.

### Clickable party link

`C_Map.GetUserWaypointHyperlink()` returns a world-map link. A party message can offer the current guide stop, and a click can set that person’s own pin, including for someone without this addon. One link at a time matches the one-waypoint limit. Whether Forever’s chat keeps an addon-sent map link is unverified.

### World flares

Eight light columns can be placed with `/worldmarker` or `/wm`: blue square, green triangle, purple diamond, red cross, yellow star, orange circle, pale moon, and white skull. `PlaceRaidMarker` is listed for Forever 1.60.1. The world-marker article says any member of a 5-person party can place them. The macro notes say a player must be in a group, and that a raid allows only the leader or an assistant. Everyone in the group sees the column, with or without this addon. Six course stops fit, with two symbols left over.

`PlaceRaidMarker` is protected. It opens a ground cursor, and a real click puts the flare down. Addon code cannot stamp the eight symbols onto the checkpoint coordinates. There is also no supported way for an addon to read a flare’s position back, so a flare cannot be what awards a shard. A secure button can offer `/wm` once someone is already standing in a rectangle. That is a setup aid for a gathering.

### Pings

Ping APIs are protected. A ping fades in seconds, and one is current. Players can still ping by hand during a game. The addon should leave that alone.

DLL tools that inject markers at raw coordinates, and older 3D drawing addons, are outside this port.

## What the first edition is for

The first Forever files, once a live survey agrees, keep v0.72 scoring and add the personal pins plus the moving guide. Party links and a flare button join only if that survey shows they work. Neither one awards shards. `/iceflow end` and the finish clear only a waypoint this addon set.

No saved variables, no addon-comm library, and no shared scoreboard. Secret-value guards and item-ID scans are compatibility work. They are not new rules.

## What stays open

- A required order, or a requirement to visit all four middle stops. The guide may prefer the nearest remaining stop.
- Penalties counted in real seconds rather than poll ticks.
- Distance to every teammate, rather than the current target.
- A shared scoreboard or an automatic winner.
- Dropping the local “Distance ok!” line that v0.72 prints on every passing check. The penalty warning would remain. That quieter line is a proposal.

## What a live client still has to answer

The survey needs a Forever install and, for the ball, a second player. Record the build, `WOW_PROJECT_ID`, and `select(4, GetBuildInfo())`.

- Which TOC suffix loads: `TheGreatIceflowRelay_Camelot.toc` is the documented flavor name. Add `_Forever.toc` only if this build looks for that name.
- Map ID, x, y, zone text, and subzone text while standing on all six landmarks. Adjust rectangles only from those readings.
- From the center of one stop, set a user waypoint, super-track it, and note what is actually visible.
- Post that hyperlink to party chat from addon code and click it on the second client.
- Place one `/wm` flare in a party and confirm the other player sees it. Check the same action in a raid as a non-assistant.
- Throw item 18662 both ways. Log `ITEM_PUSH`, `BAG_UPDATE_DELAYED`, the icon file ID, and the count before and after.
- Measure `CheckInteractDistance` indices 1–4 at a known spacing, in and out of combat, and note any secret returns.
- Send one ordinary party line from an addon and confirm it arrives.

## Sources

The claims above come from public pages read on 2026-11-19, not from a logged-in Forever client.

- Warcraft Wiki: [PlaceRaidMarker](https://warcraft.wiki.gg/wiki/API_PlaceRaidMarker), [C_Map.SetUserWaypoint](https://warcraft.wiki.gg/wiki/API_C_Map.SetUserWaypoint), [C_SuperTrack.SetSuperTrackedUserWaypoint](https://warcraft.wiki.gg/wiki/API_C_SuperTrack.SetSuperTrackedUserWaypoint), [worldmarker macro](https://warcraft.wiki.gg/wiki/MACRO_worldmarker), [World Marker](https://warcraft.wiki.gg/wiki/World_Marker), [C_PingSecure.SendPing](https://warcraft.wiki.gg/wiki/API_C_PingSecure.SendPing), [Patch 1.60.1/API changes](https://warcraft.wiki.gg/wiki/Patch_1.60.1/API_changes), [Forever map comparison](https://warcraft.wiki.gg/wiki/Forever_map_comparison).
- wowlua, Camelot 1.60.1 documentation: [ITEM_PUSH](https://wowlua.dev/api/events/ITEM_PUSH), [BAG_UPDATE](https://wowlua.dev/api/events/BAG_UPDATE), [C_Map.GetPlayerMapPosition](https://wowlua.dev/api/C_Map/GetPlayerMapPosition), [CheckInteractDistance](https://wowlua.dev/api/global/CheckInteractDistance).
- Item 18662 listings, including [Wowhead Forever](https://www.wowhead.com/forever/item=18662/heavy-leather-ball) and [Questing.wiki](https://questing.wiki/wow-forever/items/18662/).
- Dun Morogh zone comparisons, including [foreverdiff](https://foreverdiff.com/zones/dun-morogh-1/) and the [warcraftmaps zone 1426](https://warcraftmaps.com/zone/1426/dun-morogh) guide.

Those pages can change with a patch. The live survey is what confirms them.
