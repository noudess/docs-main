The Lua Parser is a quest parser for EQEmu that uses the Lua embedded programming language.

We use Lua 5.1 so the [Lua 5.1 Manual](http://www.lua.org/manual/5.1/manual.html) applies. Section 2 is a bit of a dense read but may be of particular Integererest to those just getting started with Lua.

The rest of this guide assumes you know Lua 5.1, if you don't then it wont make sense at parts and you'll end up asking stupid questions so please learn it before you go further.

## Table of Contents
* [Init Scripts](#init-scripts)
* [NPC Scripts](#npc-scripts)
* [Player Scripts](#player-scripts)
* [Item Scripts](#item-scripts)
* [Spell Scripts](#spell-scripts)
* [Encounter Scripts](#encounter-scripts)
* [NPC Events](#npc-events)
* [Player Events](#player-events)
* [Item Events](#item-events)
* [Spell Events](#spell-events)
* [Encounter Events](#encounter-events)
* [API](#api)
* [Examples](#examples)

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
* ./quests/global/items/item_script.lua
* ./quests/zone/items/default.lua
* ./quests/global/items/default.lua

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
* ./quests/global/spells/spell_id.lua
* ./quests/zone/spells/default.lua
* ./quests/global/spells/default.lua

<a name="wiki-encounter-scripts"></a>
### Encounter Scripts
Encounter scripts are quest scripts that are only loaded after explicitly called with:

`eq.load_encounter("encounter_name")`

They will load one and only one from the following location. Which ever it finds first in the following order:
* ./quests/zone/encounters/name.lua
* ./quests/global/encounters/name.lua

Encounter scripts listen for specific events from other script types with the following functions:

```
Void register_npc_event(String name, Integer evt, Integer npc_id, luafunction func);
Void register_player_event(String name, Integer evt, luafunction func);
Void register_item_event(String name, Integer evt, Integer item_id, luafunction func);
Void register_spell_event(String name, Integer evt, Integer spell_id, luafunction func);

Note: Passing a value of -1 for npc, item or spell id to watch will watch every npc, item or spell for those events.
```

Note: 
* Encounter scripts cannot properly catch EVENT_COMMAND or EVENT_TRADE unless an existing quest is already listening for them.
* Encounter scripts also run before any normal script.
* Encounter scripts can not currently return a non-zero value back to the server for the events that use them (I would like to change this at some point but it requires more planning).

<a name="wiki-npc-events"></a>
### NPC Events

* event_say
> Triggered when a client has a npc targeted, the npc is not in combat and they /say something.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> 	String message;
> 	Integer language;
> }
> ```

* event_trade
> Triggered when a client trades money or items to a npc.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> 	Trade trade;
> }
> ```
> The Trade table has the following structure:
> ```
> {
> 	ItemInst item1;
> 	ItemInst item2;
> 	ItemInst item3;
> 	ItemInst item4;
> 	Integer copper;
> 	Integer silver;
> 	Integer gold;
> 	Integer platinum;
> }
> ```

* event_death
> Triggered when the npc dies.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Mob other;
> 	Integer damage;
> 	Spell spell;
> 	Integer skill_id;
> }
> ```
> Returning a non-zero value from this function will cancel the death

* event_spawn
> Triggered when the npc spawns for the first time.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> }
> ```

* event_combat
> Triggered when the the combat state of a npc changes
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Boolean joined;
> }
> ```

* event_slay
> Triggered when this npc slays an enemy
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Mob other;
> }
> ```

* event_waypoint_arrive
> Triggered when this npc arrives at a grid waypoint
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Integer wp;
> }
> ```

* event_waypoint_depart
> Triggered when this npc departs from a grid waypoint
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Integer wp;
> }
> ```

* event_timer
> Triggered when a timer attached to this npc is triggered
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	String timer;
> }
> ```

* event_signal
> Triggered when this npc receives a signal
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Integer signal;
> }
> ```

* event_hp
> Triggered when this npc falls below the last hp event or rises above the last inc hp event.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Integer hp_event;
> 	Integer inc_hp_event;
> }
> ```

* event_enter
> Triggered when a client enters our set proximity.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> }
> ```

* event_exit
> Triggered when a client exits our set proximity.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> }
> ```

* event_cast_on
> Triggered when a spell is cast on this npc.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Spell spell;
> }
> ```

* event_aggro_say
> Triggered when a client has a npc targeted and they /say something.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> 	String message;
> 	Integer language;
> }
> ```

* event_proximity_say
> Triggered when a client has a npc targeted, the npc is not in combat and they /say something.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> 	String message;
> 	Integer language;
> }
> ```

* event_cast
> Triggered when this npc finishes casting a spell.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Spell spell;
> }
> ```

* event_cast_begin
> Triggered when this npc begins casting a spell.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Spell spell;
> }
> ```

* event_target_change
> Triggered when this npc has its' target change.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Mob other;
> }
> ```

* event_hate_list
> Triggered when a target is added/removed to/from this npc's hatelist.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Boolean joined;
> }
> ```

* event_feign_death
> Triggered when a client attempts to feign death against this npc.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> }
> ```
> Returning a non-zero value will cancel the feign death

* event_task_accepted
> Triggered when a client accepts a task offered by this npc.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Client other;
> 	Integer task_id;
> }
> ```

* event_enter_area
> Triggered when a npc enters an area defined by the quest system.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Integer area_id;
> 	Integer area_type;
> }
> ```

* event_leave_area
> Triggered when a npc leaves an area defined by the quest system.
> Passes an event table as an argument:
> ```
> {
> 	NPC self;
> 	Integer area_id;
> 	Integer area_type;
> }
> ```

<a name="wiki-player-events"></a>
### Player Events

* event_say
> Triggered when a client /says something.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	String message;
> 	Integer language;
> }
> ```

* event_death
> Triggered when a client dies.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Mob other;
> 	Integer damage;
> 	Spell spell;
> 	Integer skill;
> }
> ```
> Returning a non-zero value will cancel the death.

* event_timer
> Triggered when a timer attached to this client expires.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	String timer;
> }
> ```

* event_signal
> Triggered when a client is signaled.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer signal;
> }
> ```

* event_enter_zone
> Triggered when a client enters the zone.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_click_door
> Triggered when a client clicks on a door.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Door door;
> }
> ```

* event_loot
> Triggered when a client loots an item.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	ItemInst item;
> }
> ```

* event_zone
> Triggered when a client attempts to zone to a new zone.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer zone_id;
> }
> ```

* event_level_up
> Triggered when a client levels up.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_task_stage_complete
> Triggered when a client completes a task stage.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer task_id;
> 	Integer activity_id;
> }
> ```

* event_task_update
> Triggered when a client has a task update progress.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer task_id;
> 	Integer activity_id;
> 	Integer count;
> }
> ```

* event_task_complete
> Triggered when a client has a task complete.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer task_id;
> 	Integer activity_id;
> 	Integer count;
> }
> ```

* event_task_fail
> Triggered when a client has a task fail.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer task_id;
> }
> ```

* event_player_pickup
> Triggered when a client picks an item up.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	ItemInst item;
> }
> ```

* event_popup_response
> Triggered when a client picks an item up.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer popup_id;
> }
> ```

* event_cast
> Triggered when a client finishes casting a spell.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Spell spell;
> }
> ```

* event_cast_begin
> Triggered when a client starts casting a spell.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Spell spell;
> }
> ```

* event_target_change
> Triggered when a client changes their target.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_combine_success
> Triggered when a client successfully combines a tradeskill recipe.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer recipe_id;
> 	String recipe_name;
> }
> ```

* event_combine_failure
> Triggered when a client fails to combine a tradeskill recipe.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer recipe_id;
> 	String recipe_name;
> }
> ```

* event_group_change
> Triggered when a client changes their group.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_forage_success
> Triggered when a client forages an item.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	ItemInst item;
> }
> ```

* event_forage_failure
> Triggered when a client fails to forage an item.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_fish_start
> Triggered when a client starts to fish.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_fish_success
> Triggered when a client catches something while fishing.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	ItemInst item;
> }
> ```

* event_fish_failure
> Triggered when a client fails to catch something while fishing.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_click_object
> Triggered when a client clicks on an object.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Object object;
> }
> ```

* event_discover_item
> Triggered when a client discovers an item (eg: the item is first seen on the server by this player).
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Item item;
> }
> ```

* event_disconnect
> Triggered when a client disconnects from the server.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_connect
> Triggered when a client zones in for the first time from world.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> }
> ```

* event_duel_win
> Triggered when a client wins a duel.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Client other;
> }
> ```

* event_duel_lose
> Triggered when a client loses a duel.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Client other;
> }
> ```

* event_command
> Triggered when a client enters a #command.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	String command;
> 	StringArray args;
> }
> ```
> Returning a non-zero value will suppress the command not found message

* event_feign_death
> Triggered when a client feigns death.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	NPC other;
> }
> ```
> If a non-zero value is returned from this function then the feign death is canceled in the same way it is on the NPC version of event_feign_death.

* event_enter_area
> Triggered when a client enters an area defined by the quest system.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer area_id;
> 	Integer area_type;
> }
> ```

* event_leave_area
> Triggered when a client leaves an area defined by the quest system.
> Passes an event table as an argument:
> ```
> {
> 	Client self;
> 	Integer area_id;
> 	Integer area_type;
> }
> ```

<a name="wiki-item-events"></a>
### Item Events

* event_timer
> Triggered when a timer attached to this item expires.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	String timer;
> }
> ```

* event_scale_calc
> Triggered on a timer every 10 seconds for a scaling item.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> }
> ```

* event_item_enter_zone
> Triggered when a client enters the zone with this item.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> }
> ```

* event_item_click
> Triggered when a client right clicks an item. Only works on SoF+ clients.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	Integer slot_id;
> }
> ```

* event_item_click_cast
> Triggered when a client right clicks an item to cast a spell with it.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	Integer slot_id;
> }
> ```
> Returning a non-zero value from this function will cause the spell effect attached to the clicky item to not trigger.

* event_item_tick
> Triggered by a timer every 10 seconds randomly (driven by a db table).
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> }
> ```

* event_drop_item
> Triggered when a client attempts to drop an item on the ground.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> }
> ```
> Returning a non-zero value will make the item not actually be dropped on the ground.

* event_destroy_item
> Triggered when a client attempts to destroy an item on the ground.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> }
> ```

* event_weapon_proc
> Triggered when a client procs when using this item.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	Mob target;
> 	Spell spell;
> }
> ```
> Returning a non-zero value from this function will cause the proc spell to not cast at all.

* event_loot
> Triggered when a client loots this item from a corpse
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	Corpse corpse;
> }
> ```

* event_augment_item
> Triggered when a client augments this item.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	ItemInst aug;
> 	Integer slot_id;
> }
> ```

* event_unaugment_item
> Triggered when a client unaugments this item.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	ItemInst aug;
> 	Integer slot_id;
> }
> ```

* event_augment_insert
> Triggered when a client inserts this item into another as an augment.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	ItemInst item;
> 	Integer slot_id;
> }
> ```

* event_augment_remove
> Triggered when a client inserts this item into another as an augment.
> Passes an event table as an argument:
> ```
> {
> 	ItemInst self;
> 	Client owner;
> 	ItemInst item;
> 	Integer slot_id;
> 	Booleanean destroyed;
> }
> ```

<a name="wiki-spell-events"></a>
### Spell Events

* event_spell_effect
> Triggered when a spell affects a target.
> Passes an event table as an argument:
> ```
> {
> 	Spell self;
> 	Mob target;
> 	Integer buff_slot;
> 	Integer caster_id;
> }
> ```

* event_spell_buff_tic
> Triggered when a spell tics on a target.
> Passes an event table as an argument:
> ```
> {
> 	Spell self;
> 	Mob target;
> 	Integer tics_remaining;
> 	Integer caster_level;
> 	Integer buff_slot;
> 	Integer caster_id;
> }
> ```

* event_spell_fade
> Triggered when a spell fades from a target.
> Passes an event table as an argument:
> ```
> {
> 	Spell self;
> 	Mob target;
> 	Integer buff_slot;
> 	Integer caster_id;
> }
> ```

* event_spell_effect_translocate_complete
> Triggered when a translocate spell completes.
> Passes an event table as an argument:
> ```
> {
> 	Spell self;
> 	Mob target;
> }
> ```

<a name="wiki-encounter-events"></a>
### Encounter Events

* event_encounter_load
> Triggered when an encounter is set to load.
> Passes an event table as an argument:
> ```
> {
> 	String name;
> }
> ```

* event_encounter_unload
> Triggered when an encounter is set to unload.
> Passes an event table as an argument:
> ```
> {
> 	String name;
> }
> ```

<a name="wiki-api"></a>
### API
* [Lua API](Lua-API)

<a name="wiki-examples"></a>
### Examples
* [Lua Examples](Lua-Examples)