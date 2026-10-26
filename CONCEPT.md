# The Great Iceflow Relay — creative concept

**Creative author:** Babuni.dev  
**Format:** cooperative/competitive in-world roleplay event supported by a small World of Warcraft 1.12 addon.

## Where the idea began

The creator explains the motivation in their own words in [README.md](README.md): they enjoyed **throwing a ball around in WoW**, but simply passing it back and forth began to feel stale. Instead of replacing the social activity with a separate video game, they imagined rules for playing with that existing object in the game world.

That creative leap—to turn an informal player ritual into a structured relay with an actual course, points and consequences—belongs to Babuni.dev. The original README also openly acknowledges AI assistance with **coding**. This is one of the clearest first-person records of the project's creative authorship, so preserve its voice.

## The experience the project aims for

Friends gather at **Iceflow Lake in Dun Morogh**, near Brewnall Village, and pass a **Heavy Leather Ball** while navigating a six-stop course. The activity balances two impulses: collect **Iceflow Shards** through catches and intermediate stops; avoid penalties by passing quickly and spreading out. A finish message turns the improvised chase into a memorable group moment.

The original description proposes pairs or small groups, including three people passing multiple balls in a triangle. That is an **event concept**: the addon is currently per-player, and participants still organize the shared physical game themselves.

## Design pillars

- **In-world play:** use the actual lake, the actual game item, game emotes and social proximity.
- **Lightweight invitation:** chat commands and printed coordinates, no custom arena or complex UI.
- **Roleplay before competitive rigor:** the joy of the activity matters more than a perfectly synchronized esport rules engine.
- **Visible consequences:** catches and checkpoint entries build shards; holding and closeness lead to penalties.
- **Player ownership:** the creator's course and rules define the activity; AI-assisted technical execution is a separate contribution.

## Boundaries and accuracy

This is not a stand-alone game or automated group tournament. Current code uses local state on each client and does not authenticate ball transfers between players, enforce the checkpoint order or identify every nearby teammate. Those gaps do not erase the original concept; they are part of the development story. See [architecture](docs/ARCHITECTURE.md) and [design decisions](docs/DECISIONS.md).

The repository records a 0.72 addon. No in-game multiplayer validation occurred during the 2026-10-26 documentation reconstruction.
