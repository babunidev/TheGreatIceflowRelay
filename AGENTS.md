# The Great Iceflow Relay — contributor and AI guidelines

**Creative and project owner:** Babuni  
**Repository:** `babunidev/TheGreatIceflowRelay`

## Preserve the identity of the game

The Great Iceflow Relay is a **gnomish ball-passing game at Iceflow Lake in World of Warcraft**, born from throwing a ball back and forth with the creative's brother. Players ran, jumped and passed the item; the lack of ways to stop it in flight inspired a relay built on movement, passing, checkpoints, shards and penalties.

The creative conceived the game and directed its rules. AI assisted with Lua implementation and later with documentation. Do not attribute the original game idea to AI or describe this project as an ordinary racing addon.

## Documentation voice

- Write public-facing history **in the creative's first-person perspective**. Use `I` and `my` naturally inside sentences, but **never begin a sentence with “I” or “My.”**
- Prefer `creative`, not `creator`, as the role label for a person who conceived or made the work.
- Write for people: concise paragraphs, clear headings, concrete examples and a natural voice. Avoid promotional copy and unnecessary technical repetition.
- Distinguish the creative's direction, AI's contributions, tested results, proposed ideas and actual implementation.
- Never imply the creative personally wrote AI-generated code, or that AI suggested an idea the creative supplied.
- Label incomplete older history **retrospective reconstruction**; preserve important disagreements, decisions and uncertainties without fabricating a conversation.
- Historical source content can be linked in Git history instead of silently paraphrasing it as a quotation.

## Technical boundaries

- Original source: WoW 1.12, interface `11200`, Lua 5.0-style code, version `0.72`.
- Preserve the existing Lua/TOC behavior unless implementation is explicitly requested.
- Its checkpoint/ball/penalty loop polls approximately every two seconds; per-player scores are local.
- Catch recognition uses `ITEM_PUSH` and a throwing-ball icon check; inventory checks use the English item name.
- Distance penalties depend on the current target, not a scan of the group.
- The future modern-client edition is a **creative goal**, not established API compatibility. Verify the intended client, available ball interaction and restrictions before proposing an implementation.

## Workflow and verification

1. Read `README.md`, `CONCEPT.md`, `docs/DECISIONS.md`, `docs/ARCHITECTURE.md`, the Lua source and TOC before changing mechanics.
2. Keep proposals separate from decisions explicitly made by the creative.
3. Check the actual repository state before claiming an implementation or test.
4. For substantive code changes, update affected documentation, including `CHANGELOG.md`, `docs/DEVLOG.md` and `docs/DECISIONS.md`.
5. Record tested client/build, steps, expected/observed behavior and commit when available. Static inspection is not a gameplay test.
6. Preserve the license, historical credits and publication safety. Never expose private chat logs, secrets or personal information.
