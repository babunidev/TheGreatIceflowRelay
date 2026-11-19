# The Great Iceflow Relay — human–AI collaboration

Follow [the documentation standard](DOCUMENTATION.md) for first-person author voice throughout project documentation, factual changelogs, and naming the AI tool and verified model for each contribution.

**AI contribution:** Original coding assistance acknowledged in the 2025 README; later technical reviews and documentation revisions.

## Where the game came from

Throwing a ball around World of Warcraft with my brother led to the question of whether we could turn it into a proper game. Running, jumping and passing were already fun, but the inability to stop a ball mid-flight meant the rules had to be different from an ordinary sport. That limitation inspired my relay around Iceflow Lake: checkpoints, catches, shards and penalties.

The relay, its social purpose and its gnomish setting came from me.

## How AI contributed

The [original 2025 README](https://github.com/babunidev/TheGreatIceflowRelay/blob/03b275d/README.md) explicitly acknowledges AI help with Lua coding. That is evidence of implementation assistance, not a detailed map of who wrote or suggested every line. The surviving Git history records frequent technical revisions but not a complete conversation, list of rejected proposals or full test log.

On **26 October 2026**, AI inspected the source and Git history to build a more substantial documentation set. It described code behavior and limitations without changing the runtime. On **1 November 2026**, I supplied additional personal recollections and the intention to investigate a modern WoW version; AI revised the writing and technical references to reflect those choices.

## What the project record should distinguish

- **Creative direction:** The human creative's own idea, setting, goals, rules and decisions.
- **AI assistance:** Research, coding, editing and technical analysis actually carried out by AI.
- **Iteration:** Approaches visible in commits, with motives identified only when supported.
- **Decisions:** Explicitly confirmed choices versus suggestions still under discussion.
- **Implementation:** Files and commits that actually changed.
- **Verification:** Tests that actually ran, including client/build, steps and observations.

Documentation changes do not establish game compatibility. An intended modern-client port is not an implemented modern-client port. Preserve that distinction in every future update.

Historical gaps should be named as **retrospective reconstruction**, never filled by imagined quotes, test outcomes or conversations. Keep published documentation free of private chats, personal details and credentials.

## 18 November 2026 — Collaboration record review

At my request, Codex (GPT-6) revised this record for first-person voice and checked the attribution against the available repository documentation. Where an earlier AI tool or model is missing from the record, its identity remains unconfirmed.

## 19 November 2026 — Forever feasibility

The choice of WoW Forever, and the wish for markers players can see at the checkpoints, came from me. Cursor (Grok 4.7) researched public addon APIs, item listings, and zone comparisons, then drafted the roadmap, [the feasibility note](FOREVER.md), and the related updates. That work separated three marker systems: personal pins and one tracked waypoint, clickable party links, and world flares that a player places by hand. It also recorded the calls the 1.12 file cannot make on Forever.

No gameplay file changed, and no client test was run. Where a wiki lists an API for Forever 1.60.1, the note says so. Where the behavior still depends on standing in the zone, the note leaves it for a later survey.
