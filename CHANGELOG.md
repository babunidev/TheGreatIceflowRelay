# The Great Iceflow Relay — changelog

**Creative:** Babuni

## 2026-11-19 — human–AI collaboration record

- Rewrote `docs/AI_COLLABORATION.md` to the shared text used in all of Babuni's repositories: how Babuni works with AI, who did what (the tools and recorded models named in this project's records) and where the details are. The earlier, longer version stays in the Git history. Claude Code (Claude Opus 5.5).

## 2026-11-19 — WoW Forever roadmap

- Named WoW Forever as the intended client for a separate edition.
- Added a feasibility note that keeps the 1.12 scoring rectangles and plans visible course guidance: map pins, one tracked waypoint, and hand-placed world flares beside those zones.
- Updated the roadmap, decisions, architecture pointer, README status, concept, design note, documentation map, contributor guidance, development journal, and collaboration record.
- **Documentation only:** no Lua, TOC, or license changes, and no game-client test. Cursor (Grok 4.7).

## 2026-11-19 — documentation moved into `docs/`

- Moved `CONCEPT.md` and `ROADMAP.md` into `docs/`. The root keeps only `README.md`, `AGENTS.md`, `LICENSE` and `CHANGELOG.md`; links to the moved files and the documentation rules in `AGENTS.md` were updated. No code changed. Claude Code (Claude Opus 5.5).

## 2026-11-01 — documentation revision

- Rewrote the public documentation for readability and a consistent human-first narrative.
- Added the creative's first-person recollection of throwing the ball with his brother, moving and jumping while passing, and designing around the inability to stop a thrown ball in flight.
- Clarified the game rules, local scoring, implementation limitations and the original gnomish Iceflow Lake setting.
- Recorded the intention to investigate a modern WoW adaptation without presenting a port as feasible, approved in detail or implemented.
- Updated the development journal, decision record, collaboration history, roadmap and contributor guidance to match the babuni.dev documentation conventions.
- **Documentation only:** no gameplay code, addon manifest or license changes; no game-client tests.

## 2026-10-26 — historical documentation reconstruction

- Expanded the concept, architecture, game-course reference, design notes, decision record, journal and collaboration methodology.
- Distinguished the original event description from source behavior: per-client scoring, unordered checkpoints, target-only proximity checks and two-second penalty polling.
- Standardized author attribution to the then-used Babuni.dev credit.
- **Documentation only:** no Lua or TOC edits and no game-client verification.

## Earlier repository history

| Date | Evidence | Change visible in history |
| --- | --- | --- |
| 2025-09-11 | `5ffa935`, `5c86d98` | TOC and first Lua source; early checkpoint geometry used triangles. |
| 2025-09-11 | `be7d9d0`, `55cc340` | Course and run handling evolved toward rectangles, start/finish states and inventory checks. |
| 2025-09-12–13 | `957f4a1`, `39a85fd` | Item-receipt rewards and penalty/finish arithmetic evolved. |
| 2025-09-13 | `ab474ad`, `6b69b48` | Finish messaging and raid chat support were refined. |
| 2025-09-16–17 | `2f03b91`, `3e04880`, `03b275d` | Help text, original README and marked-course-map link appeared. |
| 2026-09-18 | `8c91d36` | Descriptions became neutral about WoW 1.12 server providers. |

Many early commits have generic messages. Their code changes are evidence; individual motivations and exact test outcomes are not recoverable from their titles alone.
