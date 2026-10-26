# The Great Iceflow Relay — roadmap

**Creator:** Babuni.dev  
**Interpretation:** This is an evidence-based verification backlog, **not** a promise or approval of new features.

## Present source baseline

- The manifest advertises addon version **0.72**, WoW interface **11200**.
- Six checkpoint rectangles in Dun Morogh; start and finish near Brewnall Village.
- Local score made of catch/checkpoint shards minus inventory-hold and target-distance penalties.
- `/iceflow` commands, party/raid chat summaries and item receipt handling.
- No test suite is present in the inspected repository.

## First: verify the existing game in-client

- Install on the target 1.12-compatible client and confirm slash command registration and rules display.
- Travel the [six checkpoints](docs/CONTENT.md) and test detection near rectangle edges.
- Check the Heavy Leather Ball's item name and `ITEM_PUSH` icon payload on the actual client.
- Verify catch shard awards, inventory penalty timing, score arithmetic and finishing behavior.
- Test two clients in a party, then raid, documenting what each participant sees.
- Verify `CheckInteractDistance` thresholds and how NPC/teammate targets affect penalties.
- Test starting, ending, restarting and re-arming while inside the starting rectangle.

## Then: decisions for the creator, not established requirements

1. Should participants be **required to visit all four middle checkpoints**, and in a fixed order?
2. Should the proximity rule be about the **current target** or truly about **all teammates**? If the latter, is it technically feasible in the client?
3. Does holding the ball cost a point **per polling tick**, per full second, or only after a grace period?
4. Should a future edition have a synchronized group scoreboard, referee mode or standings?
5. Should the route map, checkpoint markers and on-screen status be available inside the game?

None of these decisions is recorded as accepted. Keep v0.72 behavior stable until the creator chooses which, if any, changes to pursue.

## Completion criteria for a future verified release

Record exact client build, party size, route, observed shard and penalty transitions, expected vs actual results, and a tested commit. A static code review is insufficient to mark gameplay verified.
