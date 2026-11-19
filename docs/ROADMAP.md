# The Great Iceflow Relay — roadmap

**Creative direction:** Babuni  
**Source baseline:** v0.72 for World of Warcraft 1.12.  
**Intended next client:** WoW Forever (1.60.1, interface 16001, codename Camelot).  
**Status:** Original game preserved. A Forever edition is planned and not built. The 2026-11-19 API notes are public research, not an in-game test.

## 1. Preserve the original game — completed as documentation

- [x] Record the ball-passing origin with my brother and the limits that inspired the rules.
- [x] Document the six course locations, scoring system, commands and original game concept.
- [x] Identify where source behavior differs from the intended social rules.
- [x] Preserve dated development history and distinguish AI coding assistance from creative direction.

These checkmarks refer to **documentation**, not verified modern-client gameplay.

## 2. Verify the legacy source — not yet done

- [ ] Test the addon on a specified 1.12-compatible client and record the client build.
- [ ] Verify start/finish boundaries, all four intermediate checkpoints and repeated runs.
- [ ] Test the Heavy Leather Ball transfer, `ITEM_PUSH` payload, shard award and bag-holding penalties.
- [ ] Check the target-distance behavior with teammates, other players and NPC targets.
- [ ] Observe party/raid announcements and compare scores across two or more clients.
- [ ] Document any discrepancies with reproducible observations rather than assumptions.

## 3. Choose WoW Forever and record what it can do — research written, not played

Finding the checkpoint was always the difficult moment in a run. The rectangles award the shards, and nothing on the ground shows where they are. WoW Forever is the client I want for the next edition: the same lake, the same ball, and a guide on top of those zones.

- [x] Name WoW Forever as the intended client. Public sources describe client 1.60.1, interface 16001, and the Camelot codename.
- [x] Confirm from public item data that Heavy Leather Ball (item 18662) is still described as a throwable catch item.
- [x] Compare the v0.72 calls with published Forever addon APIs: bags, item receipt, map position, chat, secret values, and group markers. Details are in [the feasibility note](FOREVER.md).
- [x] Separate what an addon can show from what it cannot place. Scoring stays on the rectangles. Pins and one tracked waypoint are the intended guide.
- [ ] Survey a live Forever client: build, TOC flavor, the six landmarks, a real throw, distance checks, a party waypoint link, and one world flare.
- [ ] Build a separate Forever edition without changing the 1.12 files.
- [ ] Play one full lap on two clients and record what actually happened.

These checked items are **public-source research and creative direction**, not a playtest. Published zone comparisons describe Dun Morogh as unchanged from Classic Era, so the v0.72 rectangles are the survey’s starting points. They are not yet confirmed in a Forever client. UiMapID **1426** is a working hypothesis for `C_Map`.

## 4. First Forever edition — not yet built

After the live survey, the new files stay beside the legacy pair. The repository root is the addon folder.

- `TheGreatIceflowRelay_Camelot.toc` with interface **16001**, loading `forever/TheGreatIceflowRelay.lua`. Add `_Forever.toc` only if that build looks for that suffix instead.
- A separate version line, for example `0.1.0-forever`, so the new file is not confused with preserved v0.72.

Scoring stays the v0.72 game: `/iceflow` commands, arm, start rectangle, four once-each shards in any order, a catch shard when the count of item 18662 increases, one holding penalty per poll, one proximity penalty on the current target, a local score, and party or raid announcements.

Guidance is the accepted gameplay addition:

- Map and minimap pins for all six centers. Visited pins dim.
- One super-tracked user waypoint: the start, then the nearest middle stop not yet collected, then the finish. A different order still scores. The arrow is a guide.
- A party chat link for the current guide stop, only if the survey shows Forever keeps an addon-sent map link.
- A secure button that offers `/wm` while the player is standing in a checkpoint, only if flares work in that group. The button does not award shards.
- `/iceflow end` and the finish clear only a waypoint this addon set.

No saved variables, no addon-comm library, no shared scoreboard, and no injected world markers. Dropping the “Distance ok!” line on every passing check is still only a proposal. The penalty warning would stay.

## 5. Open design questions

- Should a future relay require all four intermediate checkpoints, and in what order? The guide may point at the nearest remaining stop, and a different order still counts.
- Should holding penalties be based on actual elapsed time rather than polling ticks?
- Can teammate proximity be checked reliably, or should a modern edition use a different fair-play rule?
- Is a shared scoreboard necessary, or should scores remain local with a human referee?
- Should the “Distance ok!” line on every passing check be dropped, while the penalty warning stays?

These are questions for future evaluation, **not accepted feature changes**. The first Forever edition keeps the rectangles. Flares, pings, and the single waypoint are guidance around those zones.

## Verification standard

For every future implementation, record the exact client/build, test setup, players involved, expected behavior, observed behavior, affected files and commit. Do not describe a code-only review or a public API note as an in-game test.
