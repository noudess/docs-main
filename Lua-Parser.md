The Lua Parser is a quest parser for EQEmu that uses the Lua embedded programming language.

We use Lua 5.1 so the [Lua 5.1 Manual](http://www.lua.org/manual/5.1/manual.html) applies. Section 2 is a bit of a dense read but may be of particular interest to those just getting started with Lua.

## Table of Contents
* [Init Scripts](#init-scripts)
* [NPC Scripts](#npc-scripts)
* [Player Scripts](#player-scripts)
* [Item Scripts](#item-scripts)
* [Spell Scripts](#spell-scripts)
* [Encounter Scripts](#encounter-scripts)
* [Events](#events)
* [API](#api)

<a name="wiki-init-scripts"></a>
### Init Scripts
On Lua Parser reload it will attempt to load two scripts with no function env.
* ./quests/zone/script_init.lua
* ./quests/global/script_init.lua

These are useful for setting up modules to load automatically or for loading encounters.

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
Player Scripts are quest scripts attached to Players.
Players will load a script on the first event that triggers them and they will load one and only one from the following location. Which ever it finds first in the following order:
* ./quests/zone/player_v[instance_version].lua
* ./quests/zone/player.lua
* ./quests/global/player.lua

Players will also attempt to load a global Player script that is attached to all Players from the following location:
* ./quests/global/player.lua

<a name="wiki-item-scripts"></a>
### Item Scripts
Item Scripts are quest scripts attached to Items.
Items will load a script on the first event that triggers them and will load one and only one from the following location. Which ever it finds first in the following order:
* ./quests/zone/items/item_script.lua
* ./quests/items/item_script.lua

The format of the item_script is as follows:
```
If ScriptFileID != 0
	item_script = "script_" + ScriptFileID
Else If CharmFile != ""
	item_script = CharmFile
Else
	item_script = item_id
```

<a name="wiki-spell-scripts"></a>
### Spell Scripts
Spell Scripts are quest scripts attached to Spells.
Spells will load a script on the first event that triggers them and will load one and only one from the following location. Which ever it finds first in the following order:
* ./quests/zone/spells/spell_id.lua
* ./quests/spells/spell_id.lua

<a name="wiki-encounter-scripts"></a>
### Encounter Scripts
Encounter scripts are quest scripts that are only loaded after explicitly called with:

`eq.load_encounter("encounter_name")`

Encounter scripts listen for specific events from other script types with the following functions:

```
void register_npc_event(std::string name, int evt, int npc_id, luafunction func);
void register_player_event(std::string name, int evt, luafunction  func);
void register_item_event(std::string name, int evt, Lua_Item item, luafunction  func);
void register_spell_event(std::string name, int evt, int spell_id, luafunction  func);
```

Note: Encounter scripts cannot properly catch EVENT_COMMAND or EVENT_TRADE unless an existing quest is already listening for them.

<a name="wiki-events"></a>
### Events

Quest scripts are event based, the following events are currently responded to by the Lua parser:

All event functions are passed one argument: an event table.
For NPCs the table will always have 'self' as the npc.
For Players the table will always have 'self' as the client.
For Items the table will always have 'self' as the item and 'owner' as the owner of the item.
For Spells the table will always have 'self' as the spell.

* event_say

Triggered when either a client says something (Player) or when a client says something with a npc targeted that is not in combat (NPC).
The event table has:
'other' as the triggering client. (NPC only)
'message' as the triggering message
'language' as the language of the triggering message

* event_trade

Triggered when a client trades with a npc
The event table has:
'other' as the triggering client
'trade' as a table within the event that includes the following fields:
item1, item2, item3, item4, copper, silver, gold, platinum

* event_death
* event_spawn
* event_attack
* event_combat
* event_aggro
* event_slay
* event_npc_slay
* event_waypoint_arrive
* event_waypoint_depart
* event_timer
* event_signal
* event_hp
* event_enter
* event_exit
* event_enter_zone
* event_click_door
* event_loot
* event_zone
* event_level_up
* event_killed_merit
* event_cast_on
* event_task_accepted
* event_task_stage_complete
* event_task_update
* event_task_complete
* event_task_fail
* event_aggro_say
* event_player_pickup
* event_popup_response
* event_proximity_say
* event_cast
* event_cast_begin
* event_scale_calc
* event_item_enter_zone
* event_target_change
* event_hate_list
* event_spell_effect
* event_spell_buff_tic
* event_spell_fade
* event_spell_effect_translocate_complete
* event_combine_success
* event_combine_failure
* event_item_click
* event_item_click_cast
* event_group_change
* event_forage_success
* event_forage_failure
* event_fish_start
* event_fish_success
* event_fish_failure
* event_click_object
* event_discover_item
* event_disconnect
* event_connect
* event_item_tick
* event_duel_win
* event_duel_lose
* event_encounter_load
* event_encounter_unload
* event_command
* event_drop_item
* event_destroy_item
* event_feign_death

<a name="wiki-api"></a>
### API
The Lua API consisted of many exported classes and some general functions.
* [Lua_Client](Lua-Client)
* [Lua_Corpse](Lua-Corpse)
* [Lua_Door](Lua-Door)
* [Lua_Client](Lua-Client)
* [Lua_Entity](Lua-EntityList)
* [Lua_Group](Lua-Group)
* [Lua_HateList](Lua-Hate-List)
* [Lua_Item](Lua-Item)
* [Lua_ItemInst](Lua-ItemInst)
* [Lua_Mob](Lua-Mob)
* [Lua_NPC](Lua-NPC)
* [Lua_Object](Lua-Object)
* [Lua_Raid](Lua-Raid)
* [Lua_Spell](Lua-Spell)
* [Lua General Functions](Lua-General-Functions)