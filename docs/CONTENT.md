# The Great Iceflow Relay — course and command reference

**Creative:** Babuni  
**Source:** The `checkpoints` table and slash commands in `TheGreatIceflowRelay.lua` v0.72.

## The course at Iceflow Lake

| Stop | Location | X range | Y range | Implemented result |
| --- | --- | --- | --- | --- |
| Start | Brewnall Village – Starting Stage | 31.30–31.50 | 44.30–44.50 | Starts armed run |
| 1 | The Tree | 32.65–32.80 | 39.10–39.25 | +1 shard once |
| 2 | Carcass Island | 34.10–34.40 | 41.80–42.10 | +1 shard once |
| 3 | Wet Log | 36.00–36.20 | 40.50–40.80 | +1 shard once |
| 4 | Behind the Branch | 34.50–35.00 | 45.50–46.00 | +1 shard once |
| Finish | Brewnall Village – Finish Stage | 31.40–31.60 | 44.70–44.90 | Reports net score |

Coordinates are **0–100 map percentages**, implemented as axis-aligned rectangles. Automatic checkpoint detection also requires the client zone text **Dun Morogh**. Checkpoints need not be visited in a specified order, and the finish currently accepts an incomplete route.

The original public course guide is the [marked map on Imgur](https://imgur.com/a/eQcNdPX). Its current availability has not been independently verified, and the image is not stored in this repository.

## Ball and scoring terms

- **Heavy Leather Ball:** the item name sought by inventory scans.
- **`INV_Misc_ThrowingBall_01`:** icon substring used for catch recognition from `ITEM_PUSH`.
- **Iceflow Shard:** one point awarded for a unique middle checkpoint or qualifying item-receipt event.
- **Penalty:** one point deducted for each active inventory-holding polling pass, and potentially one more for a close current target on that pass.
- **Net Shards:** total earned shards minus penalties; reported upon finishing.

Neither the item name nor the zone name is localized by this version. Catching is inferred from event data, not from a verified physical intercept.

## Slash commands

| Command | Result |
| --- | --- |
| `/iceflow ready` | Arm the relay, reset score and announce readiness |
| `/iceflow end` | Disarm and stop |
| `/iceflow rules` | Announce eight brief rules to the party/raid or locally |
| `/iceflow checkpoints` | Print all six rectangle bounds locally |
| `/iceflow check` | Test current position against the rectangles locally |
| `/iceflow pos` | Print current map X/Y locally |
| `/iceflow ballcheck` | Report whether a Heavy Leather Ball is present in bags |

An empty or unrecognized `/iceflow` argument prints the usage hint.

## Voice and setting

The project is an in-world gnomish game, not a simulated arena sport. Its distinctive vocabulary—**The Great Iceflow Relay**, **Iceflow Shards**, the named landmarks and the spirited finishing message—should remain recognizable in future documentation and adaptations.
