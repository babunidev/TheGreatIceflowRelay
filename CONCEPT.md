# The Great Iceflow Relay — concept

**Creative:** Babuni  
**Format:** A social ball-passing relay inside World of Warcraft, supported by a lightweight addon.

## The idea

Playing catch with my brother in WoW was surprisingly enjoyable. We would throw a ball, run about, jump and throw it back, making a game of the movement even before there were any rules. Eventually I started wondering what a *real* ball game could look like if those were the only tools available.

The game imposes its own peculiar boundaries: the ball is an inventory item, and a throw cannot be interrupted or defended against in mid-flight. Those limits ruled out many familiar ball sports. Instead of fighting the limitations, I built the competition around movement, passing, collecting points and avoiding penalties. The resulting rules are unusual because they belong to this particular world.

Iceflow Lake in Dun Morogh became the pitch. Its shores and small landmarks provided a natural course, while the nearby gnomish setting gave the competition its character and name: **The Great Iceflow Relay**. Determination to make the idea work became part of the project itself. AI helped implement the addon, and the original game reached a playable, enjoyable form.

## The game

Players begin near Brewnall Village, circulate one or more Heavy Leather Balls, and move between four intermediate checkpoints before returning to a finishing stage. A player earns **Iceflow Shards** by reaching a new checkpoint and by receiving the ball. Holding the ball during scoring checks and getting too close incur penalties. The result is the difference between shards earned and penalties collected.

The spirit of the game is social: two people can play catch across the course, while three or more can improvise patterns, even with several balls. The gnomish relay is a shared activity first and a scoreboard second.

## Design principles

- **Work with what exists.** Use WoW's ordinary movement, inventory item, throw interaction, map locations and chat.
- **Make the limitations meaningful.** Reward passing and movement rather than pretending the ball has simulated physics or defensive controls.
- **Give the world a role.** Iceflow Lake and its landmarks form the playing field.
- **Keep participation lightweight.** A few chat commands and visible announcements are enough to run an event.
- **Leave room for people.** Friends can organize passing, routes and fair play without making the addon a fully automated referee.

## What exists and what comes next

The source provides a **v0.72 addon for WoW 1.12**, with local scoring, checkpoint rectangles, inventory polling and chat messages. Its actual proximity and catch detection are narrower than the ideal social rules. See [README](README.md) and [architecture](docs/ARCHITECTURE.md) for those limitations.

A **modern WoW adaptation is intended**, subject to investigation of the target client's item mechanics and addon APIs. This is a future direction, not an implemented port or verified compatibility claim.
