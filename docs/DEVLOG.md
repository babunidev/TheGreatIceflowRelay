# The Great Iceflow Relay — development journal

**Creative creator:** Babuni.dev  
**Reconstruction date:** 2026-10-26. Evidence comes from the creator's README, GitHub history and committed Lua/TOC. Where original chat discussions are absent, this entry is explicitly **retrospective**, not a transcript.

## Before the addon: a ball and an idea

The most important piece of source material is not a formula. It is the author's own README introduction. Babuni.dev describes enjoying throwing a ball around in World of Warcraft with friends, until repeatedly passing it back and forth felt a little stale. The author wondered why that playful existing mechanic could not become a proper mini-game.

What followed was a design for an outing at Iceflow Lake: a starting point near Brewnall Village, named checkpoints around the lake, shards earned by moving and catching, penalties for lingering with the ball or getting too close, and the delight of sharing an ending with a group. The README gives the idea a clearly social purpose. It describes pairs and, for example, three people running a triangle while multiple balls circulate. Those are the creator's ideas, not features invented during this documentation pass.

The author also says, plainly, they were new to addon coding and used **AI help to put it together**. That admission is an important part of the project history: human imagination and direction shaped the play, while AI support made it practical to prototype in Lua. The old README is preserved unedited above the new technical notes; readers can encounter that voice directly.

## 11 September 2025: shape of the game emerges

GitHub shows the addon manifest committed as `5ffa935` and the first Lua as `5c86d98` on **2025-09-11**. That first Lua used five **triangular** geographic areas and geometric point-in-triangle detection. Later revisions on the same day moved to **axis-aligned rectangular** zones, introduced separate start and finish checkpoints, managed unique visited locations and incremented a shard count. This is a concrete technical transition, not a claim that the author had a formal design meeting about geometry.

The unusually long sequence of “Update TheGreatIceflowRelay.lua” commits throughout the afternoon and evening tells its own story: there was a great deal of short-cycle iteration. The commit names by themselves do not say which ideas were proposed or rejected, nor whether each change worked on the first try. The few individually inspected diffs do, however, show the game growing from location detection into a stateful relay.

By a later 11 September revision (`55cc340`), the source distinguishes a **ready/armed** state from an **active run**, adds an explicit `/iceflow ready` action and uses the first start-zone entry to begin. Other changes brought inventory scanning for a **Heavy Leather Ball** and periodic position checks. The result remained intentionally humble: a single small addon with chat output rather than an invented physical ball mechanic.

## 12–13 September 2025: catching, costs and group presentation

A revised Lua snapshot (`957f4a1`) shows the next layer: an `ITEM_PUSH` hook awarding an immediate shard on a matching ball-icon event, with a short duplicate-event guard. This was distinct from the recurring bag scan used to detect whether the player was holding a ball.

As the penalty system developed, a subtle discrepancy appeared between explanatory language and actual time accounting. The present `CHECK_INTERVAL = 2` runs a polling pass roughly every two seconds; each detected ball-holding pass increments `totalBallTime` and `totalPenalty` by exactly one. The source comment calls these seconds, but the counter behaves like **poll ticks**. The target-distance check likewise tests the **currently targeted unit**, not a continuously measured distance from every teammate. These are observations from code, not a retroactive accusation that any player misunderstood the rules.

The 13 September commits include a visible refactoring of penalty reset/finish arithmetic (`39a85fd`), followed by changes to final-score phrasing (`ab474ad`). Another change (`6b69b48`) made announcements work in raids as well as parties, keeping solo fallback in local chat. The game was becoming more legible to an audience watching the event happen, even though each character's counters stayed local.

## 16–17 September 2025: explanation becomes part of the project

The TOC received help wording and declared version **0.72**. On **2025-09-17**, the creator-facing README appeared (`3e04880`) and was edited further (`03b275d`) to include the marked course-map link. Its tone matters. Rather than presenting the addon as a polished platform, the author called it a simple, cute RP activity and openly acknowledged both the coding learning curve and the AI assistance. That is a valuable design artifact and source of authorship context, not marketing copy to overwrite.

## 2026: preservation and review

On **2026-09-18**, descriptions were adjusted to refer to compatible WoW 1.12 clients without tying the project to one provider (`8c91d36`). On **2026-10-26**, earlier documentation passes standardized **Babuni.dev** author credit and generated a small initial scaffold. That skeleton did not adequately preserve the project's iteration or explain the gap between social rules and current scoring.

The present review read the source and historical commits, retained the creator's own explanation, and developed dedicated architecture, design, content, decision and collaboration files. **No runtime code was changed**, and no game client, real ball transfer, multiplayer session, checkpoint path or addon compatibility test was executed.

## What remains open

The biggest unanswered question is not “how do we make the code more sophisticated?” It is how much mechanical enforcement Babuni.dev actually wants. An informal RP relay may benefit from human refereeing and flexibility; a strict tournament would need verified distances, robust catch detection, route-order rules and shared results. The current documentation leaves that choice with the creator and marks all proposed changes as proposals.

**Attribution and evidence discipline:** Babuni.dev supplied the human concept, world choice and authorial voice. The repository acknowledges earlier AI coding assistance without a complete contribution ledger. In this 2026 review, AI inspected and reconstructed documentation from public code and Git; no original design decision is newly credited to AI and no test outcome is invented.
