# The Great Iceflow Relay — roadmap

**Creative direction:** Babuni  
**Source baseline:** v0.72 for World of Warcraft 1.12.  
**Status:** Original game preserved; modern-client investigation planned.

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

## 3. Investigate a modern WoW edition — intended direction

- [ ] Identify the intended modern client or clients and their supported addon environment.
- [ ] Determine whether the equivalent **throwable ball** exists, can be obtained, transferred and detected by an addon.
- [ ] Research current bag, item-receipt, event, map-coordinate, zone and chat APIs.
- [ ] Establish what is protected or impossible for addons, especially ball interaction, player distance and referee automation.
- [ ] Decide whether the original six-stop course still makes sense in the target world and map.
- [ ] Produce a feasibility report separating **possible**, **requires redesign**, and **not possible with addons alone**.
- [ ] Only then scope a port, keeping its implementation separate from the preserved 1.12 release.

The goal of returning to the game on a modern client is **approved as a direction**. No particular client, API design, feature rewrite or release date has been approved.

## 4. Open design questions

- Should a future relay require all four intermediate checkpoints, and in what order?
- Should holding penalties be based on actual elapsed time rather than polling ticks?
- Can teammate proximity be checked reliably, or should a modern edition use a different fair-play rule?
- Is a shared scoreboard necessary, or should scores remain local with a human referee?
- Would better map markers or quieter chat feedback preserve the game's simplicity?

These are questions for future evaluation, **not accepted feature changes**.

## Verification standard

For every future implementation, record the exact client/build, test setup, players involved, expected behavior, observed behavior, affected files and commit. Do not describe a code-only review as an in-game test.
