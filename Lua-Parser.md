The Lua Parser is a quest parser for EQEmu that uses the Lua embedded programming language.

We use Lua 5.1 so the [Lua 5.1 Manual](http://www.lua.org/manual/5.1/manual.html) applies. Section 2 is a bit of a dense read but may be of particular interest to those just getting started with Lua.

## Table of Contents
* [NPC Scripts](#npc-scripts)
* [Player Scripts](#player-scripts)
* [Item Scripts](#item-scripts)
* [Spell Scripts](#spell-scripts)
* [Encounter Scripts](#encounter-scripts)

<a name="wiki-npc-scripts"></a>
### NPC Scripts
NPC Scripts are quest scripts that are attached to NPCs (most quests follow this format).
NPCs will load a script on the first event that triggers them (almost always the spawn event) and they will load one and only one from the following location. Which ever it finds first in the following order:
* ./quests/zone/npcid.lua
* ./quests/zone/npcname.lua
* ./quests/global/npcid.lua
* ./quests/global/npcname.lua
* ./quests/zone/default.lua
* ./quests/global/default.lua

NPCs will also attempt to load a global NPC script that is attached to all NPCs from the following location:
* ./quests/global/global_npc.lua

<a name="wiki-player-scripts"></a>
### Player Scripts

<a name="wiki-item-scripts"></a>
### Item Scripts

<a name="wiki-spell-scripts"></a>
### Spell Scripts

<a name="wiki-encounter-scripts"></a>
### Encounter Scripts