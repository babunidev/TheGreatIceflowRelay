# The Great Iceflow Relay — course and content register

**Author:** Babuni.dev  
**Source:** current six-item `checkpoints` table in `TheGreatIceflowRelay.lua`.

## Checkpoint rectangles (map coordinates 0–100)

| Stop | Location | X min–max | Y min–max | Implemented reward |
| --- | --- | --- | --- | --- |
| 1 | Brewnall Village – Starting Stage | 31.30–31.50 | 44.30–44.50 | Begin run when armed |
| 2 | The Tree | 32.65–32.80 | 39.10–39.25 | +1 shard, once per run |
| 3 | Carcass Island | 34.10–34.40 | 41.80–42.10 | +1 shard, once per run |
| 4 | Wet Log | 36.00–36.20 | 40.50–40.80 | +1 shard, once per run |
| 5 | Behind the Branch | 34.50–35.00 | 45.50–46.00 | +1 shard, once per run |
| 6 | Brewnall Village – Finish Stage | 31.40–31.60 | 44.70–44.90 | Finish message and score |

These are **map-coordinate rectangles**, not radius-in-yards zones. The code checks whether the player is in Dun Morogh before applying automatic checkpoint rewards. No route-order enforcement is implemented.

### External map

The original README provides a creator-selected visual guide: [marked Iceflow course on Imgur](https://imgur.com/a/eQcNdPX). This is a historical outgoing link, **not** a graphic committed to this repository or independently checked for current availability.

## Item and icon

- Inventory detection: literal name **`Heavy Leather Ball`** in bag item links.
- Catch detection: icon substring **`INV_Misc_ThrowingBall_01`** within the second argument of `ITEM_PUSH`.
- Chat prefix: `[Iceflow Relay]` for group game messages; `[Iceflow Ball]` for local item feedback.
- Player terms: **Iceflow Shards**, **penalty**, **net shards**.

## Command lexicon

`/iceflow ready` arms; `end` disarms; `pos` prints location; `check` tests current rectangle; `checkpoints` prints all bounds; `ballcheck` scans bags; `rules` sends eight brief rule lines to party/raid or local chat. An empty or unknown argument prints a local usage hint.

The item's name and zone strings are English literals; localized clients should be verified rather than assumed supported.
