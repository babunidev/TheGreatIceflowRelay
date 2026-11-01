# The Great Iceflow Relay — development journal

**Creative:** Babuni  
**Historical sections:** Retrospective reconstruction from the original README, source and Git history. Exact early conversations and test records are not available.

## The ball game that began with my brother

Throwing a ball back and forth with my brother was a simple pleasure in World of Warcraft. We would move around, jump and keep throwing, making our own fun out of a small inventory item. Eventually the question became irresistible: what kind of *proper ball game* could be made from those few actions?

Unlike a conventional sport, this one offered no way to stop the ball mid-flight. The rules had to fit what WoW actually allowed rather than imitate an ordinary ball game. That constraint led me toward a relay: move across the lake, pass the ball, collect shards and risk penalties for holding on too long or getting too close. Iceflow Lake near the gnomish settlement of Brewnall Village became the course.

Once the idea formed, getting it into the game became an obsession of sorts. The original README acknowledged that coding was new territory for me and that AI helped build the addon. Those were different contributions: the concept and the decision to pursue it were mine; AI helped translate the design into working Lua. The game did become playable, and, importantly, it was fun. The exact division of early coding and debugging steps is not preserved well enough to narrate them as a full transcript.

## September 2025 — finding a shape for the rules

The first committed files appeared on **11 September 2025**: the manifest (`5ffa935`) and Lua source (`5c86d98`). Looking back through the revisions, the starting approach used five triangle-shaped checkpoint regions. Later source moved to six small rectangles, distinguished a start from a finish, and added shards for unique stops. That evolution is visible in Git; the reasons behind each intermediate geometry adjustment are not fully documented.

The same early sequence introduced an armed state, a running state, the `/iceflow ready` command and inventory checks for the Heavy Leather Ball. Rather than invent a new physics system, the addon relied on the existing game world and chat messages. Many commits are simply titled “Update TheGreatIceflowRelay.lua,” so their titles cannot establish which experiment succeeded on any particular attempt.

## September 2025 — scoring the passes

The later source added `ITEM_PUSH` handling to award a shard when a matching throwing-ball icon was received, while repeated bag checks imposed a penalty for carrying the ball. This was a practical way to work with the game's item events, not a claim that the addon could inspect the entire flight of a thrown ball.

During the **12–13 September** revisions, penalty handling, the final calculation and group presentation changed. Commits including `39a85fd`, `ab474ad` and `6b69b48` show revisions to the end-of-run reporting and support for raid as well as party announcements. The published v0.72 implementation still counts ball-holding penalties by approximately two-second checks, and its proximity check only sees the current target. These limitations belong in the record rather than being disguised as fully enforced team rules.

## September 2025 — sharing the course

By **16–17 September**, the manifest carried version **0.72**, and the first public README (`3e04880`) explained the activity in an informal first-person voice. A later README revision (`03b275d`) linked the [marked course map](https://imgur.com/a/eQcNdPX). The early account already celebrated simple RP play, group passing and AI coding assistance.

## October 2026 — reconstructing the record

During an earlier documentation review on **26 October 2026**, AI examined the committed code and portions of Git history, then expanded the technical and historical documents. The source was not run in a client during that review, and no Lua or TOC behavior changed. The result was useful but still read too often as an outside description of the creative rather than a personal account.

## November 2026 — the reason behind the game

On **1 November 2026**, more of the memory behind the idea was brought into the documentation: playing catch with my brother, moving and jumping while passing, and the challenge of designing a game where nobody could stop a ball in flight. The project name, **The Great Iceflow Relay**, remains deliberate; it describes a gnomish ball game, not a generic passing utility.

The documentation was revised with AI editorial assistance to make the rules easier to understand and to keep the historical story in my perspective. A modern WoW edition is now an explicit goal to investigate. No modern port was built, no client feasibility was established and no gameplay tests were performed as part of this documentation update.
