# Game Save to Minecraft

**An open-source Skill for coding agents to migrate saved game worlds into playable Minecraft.**

[![Watch the GameSave2Minecraft demo on YouTube](https://img.youtube.com/vi/tzVSkMqvyoQ/maxresdefault.jpg)](https://www.youtube.com/watch?v=tzVSkMqvyoQ)

[Watch the 80-second demo](https://www.youtube.com/watch?v=tzVSkMqvyoQ): a V Rising
saved-castle migration captured in Minecraft, with mapped object interactions.

Supply a save and its matching local game installation. The agent investigates
the source, writes an adapter, maps objects and interactions to Minecraft, and
checks source coverage, persistence, rendering and runtime cost. A new source
game is an adapter-authoring task; it does not need an existing converter.

This repository contains the portable agent workflow and its supporting
contracts. The [research paper, reference implementation and original example](https://github.com/crabsatellite/GameSave2Minecraft)
are maintained separately by Alex Chengyu Li. Game files, personal saves and
source-game assets are supplied locally and are not distributed here.

## Install

Place the contents of this repository in your agent's supported skill directory,
in a folder named `game-save-to-minecraft`. For Codex, the resulting entrypoint is
`~/.codex/skills/game-save-to-minecraft/SKILL.md`. You can also ask your coding
agent to read [SKILL.md](SKILL.md) directly.

The Skill can be installed independently. REA is an external inspection tool;
engine-specific decoders and a Minecraft backend are selected for the actual
source and target. The reference backend currently targets Minecraft Java
1.21.1, NeoForge and Java 21.

Example request:

> Use $game-save-to-minecraft to migrate the world in my save. Investigate my local
> client and assets, generate the source adapter, map interactions to Minecraft,
> and verify source coverage, persistence, rendering and runtime cost.

## Workflow references

- [Source investigation and adapter authoring](references/source-adapters.md)
- [World contract](references/world-contract.md)
- [Interaction mapping](references/interaction-rules.md)
- [Performance and acceptance](references/performance-and-acceptance.md)
- [Planning, effort, user decisions and recovery](references/planning-and-recovery.md)
- [GameTest, packaged-client interactions and visual verification](references/runtime-verification.md)

## Origin and license

Extracted from the `skills/game-save-to-minecraft` directory in
[`crabsatellite/GameSave2Minecraft` at `15be9d9`](https://github.com/crabsatellite/GameSave2Minecraft/tree/15be9d9a498801962c69b86097906235e64319a3/skills/game-save-to-minecraft).
The initial extraction preserves the six Skill files without changes. Earlier
research and software snapshots remain in their original repositories and
publication records. This CrabMods repository maintains the Skill going forward.

Copyright 2026 Alex Chengyu Li. The Skill and its supporting references use the
[MIT License](LICENSE). The research paper and case-study materials have their
own licenses in the reference implementation repository.

Website: [crabmods.com](https://crabmods.com) · [CrabMods on GitHub](https://github.com/CrabMods)
