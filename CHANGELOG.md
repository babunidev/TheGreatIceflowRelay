# The Great Iceflow Relay — changelog

**Creative author:** Babuni.dev

## 2026-10-26 — documentation deepening (this change)

- Preserved the first-person origin story in README.
- Expanded the concept, architecture, game/course content, experience design, decisions, development journal, collaboration method, and verification roadmap.
- Clarified differences between stated event rules and source: per-client score, unconstrained checkpoint order, target-only proximity check, and two-second penalty tick.
- **Only Markdown documentation changed. No Lua or TOC edit; no gameplay test run.**

## Earlier changes confirmed by GitHub history

| Date | Evidence | Documented evolution |
| --- | --- | --- |
| **2025-09-11** | `5ffa935`, `5c86d98` | Manifest and first Lua script added; initial checkpoint areas represented as triangles. |
| **2025-09-11** | `be7d9d0`, `55cc340`, `957f4a1` | Later code visibly moved to rectangular checkpoint regions, start/finish flags, an armed/run state, bag checks, and an `ITEM_PUSH` catch reward across successive revisions. |
| **2025-09-13** | `39a85fd`, `ab474ad`, `6b69b48` | Revisions to penalty handling, finish report wording, and support for raid output alongside party output. |
| **2025-09-16–17** | `2f03b91`, `3e04880`, `03b275d` | Manifest help wording and public README, later including the course-map link. |
| **2026-09-18** | `8c91d36` | Client descriptions changed to provider-neutral World of Warcraft 1.12 terminology. |
| **2026-10-26** | Prior docs/credit commits | Author credit standardized to Babuni.dev and a minimal documentation scaffold added. |

GitHub also records many generically titled “Update TheGreatIceflowRelay.lua” commits on 2025-09-11 to 2025-09-13. They indicate rapid iteration, but each change should be tied to an actual diff before assigning a motive, test outcome or author decision.
