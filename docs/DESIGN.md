# The Great Iceflow Relay — gameplay and experience design

**Creative direction:** Babuni.dev.

## The physical play space

The lake is not decoration: its banks, obstacles and travel distances provide the playground. The start/finish at Brewnall Village make the route legible as an outing, while intermediate landmarks—The Tree, Carcass Island, Wet Log and Behind the Branch—give players places to shout, meet, pass and improvise.

The player's ball is an existing WoW item. Movement and real conversation remain in the normal game client. The addon offers lightweight structure through chat rather than taking over the interface with custom screens.

## Player journey

1. Gather friends, distribute one or more Heavy Leather Balls, and decide how to referee fair passing.
2. Find the course using `/iceflow checkpoints`, `/iceflow pos` and the [creator-linked marked map](https://imgur.com/a/eQcNdPX).
3. Arm individual copies with `/iceflow ready`; enter the starting rectangle.
4. Move between landmarks, throw and receive balls. Each newly reached middle checkpoint awards one shard; eligible `ITEM_PUSH` events award catches.
5. Avoid the recurring ball-hold and **target** proximity penalties as implemented.
6. Enter the finish rectangle and share your final tally.

This sequence describes a suggested social event flow. **The source does not mechanically require the landmark order, nor a full traversal before the finish.**

## Scoring rhythm in current source

The reward side is simple and discrete: **one shard per unique middle checkpoint** and **one per qualified ball item event**. The cost side is recurrent: **one penalty every approximately two seconds of detected bag possession** and **one per poll when the currently targeted unit is within any checked interaction range**. The net result is `earned - penalties` and can be negative.

The source description frames the spacing rule as staying 28 yards from other players, but the code only examines a single selected target. Avoid describing the current implementation as comprehensive teammate-distance validation.

## What makes it a roleplay toy

The invitation to run in pairs or make a triangle with three players is a creator-authored social invention; it gives others room to develop their own event etiquette. The “Good Game, Well Played!” finish message acknowledges shared activity even when the technical score is individual.

## Accessibility and usability considerations (unverified)

The addon relies heavily on text feedback, English item/zone names and manually entered chat commands. Route coordinates are precise but not represented by in-game waypoints. The large amount of penalty/status chat can be distracting; it should be observed during an actual event before proposing output throttling.
