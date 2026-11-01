# The Great Iceflow Relay — gameplay design

**Creative direction:** Babuni

## A sport shaped by its limitations

The first delight was already there: running, jumping and throwing a ball between people in World of Warcraft. Playing that way with my brother suggested something more structured, but the game offered no way to intercept or stop a throw in flight. A conventional ball sport would have needed mechanics that simply did not exist.

The relay makes the existing limitations into rules. A ball in somebody's bags is a reason to pass quickly; movement between landmarks is rewarded; players are encouraged to keep apart. The action stays in the real game world rather than a separate arena interface.

## The playing field

Iceflow Lake in Dun Morogh provides a gnomish course beginning and ending near Brewnall Village. The four middle landmarks—**The Tree**, **Carcass Island**, **Wet Log** and **Behind the Branch**—turn natural scenery into checkpoints. The [marked course map](https://imgur.com/a/eQcNdPX) helps players find them.

## The social game

A pair can exchange a Heavy Leather Ball while moving through the course. With three or more people, players can improvise triangles or multiple-ball passing. Each participant with the addon tracks a personal run, while party and raid announcements make catches, checkpoints and finishes part of the group activity.

A simple score is the incentive, not the whole experience: **shards from checkpoints and eligible catches, minus penalties from holding and closeness**. The finish report gives the run an ending worth celebrating.

## What version 0.72 actually checks

- A checkpoint awards **1 shard**, once per middle location per run.
- A matching `ITEM_PUSH` icon event awards **1 shard**, subject to a brief duplicate guard.
- Holding a ball in the inventory costs **1 penalty per approximately two-second check**.
- Being close to the **current target** costs **1 penalty per check**; the addon does not evaluate all teammates.
- Entering the finish location reports the score, even if intermediate stops were skipped.
- Scoring is **local to each player's addon**; chat reports are not a shared competitive authority.

A player-organized event may use its own understanding of fairness. Describe that as a social convention rather than an automatically enforced software rule.

## Usability and future considerations

The lightweight slash-command approach suits a playful RP event but depends on English names, map coordinates and chat output. The periodic penalty messages can become noisy, and rectangular checkpoint triggers can be missed during quick movement. Neither problem has been confirmed by new gameplay tests.

Any future redesign should keep the pleasure of *moving and throwing with friends* ahead of elaborate automation. The desired modern-client version remains dependent on verifying available item mechanics and addon APIs.
