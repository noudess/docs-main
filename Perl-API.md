- [Beginners Guide To Perl](#beginners-guide-to-perl)
- [Real Use Examples](#real-use-examples)
- [How Perl Quests Are Loaded](#how-perl-quests-are-loaded)
    + [NPC](#npc)
    + [Player](#player)
- [Global Scripts](#global-scripts)
    + [Player](#player-1)
    + [NPC](#npc-1)
    + [Item](#item)
    + [Spell Scripts](#spell-scripts)
- [Perl Sub Events](#perl-sub-events)
  * [Text Response Example](#text-response-example)
  * [Special Text Response Examples](#special-text-response-examples)
- [Exported Variables](#exported-variables)
- [General Quest API](#general-quest-api)
    + [**Conditionals**](#--conditionals--)
        * [**Using $npc->GetHateList();**](#--using--npc--gethatelist-----)
      - [**Function Lists**](#--function-lists--)
- [Client](#client)
- [Corpse](#corpse)
- [EntityList](#entitylist)
- [Group](#group)
- [Raid](#raid)
- [Mob](#mob)
- [NPC](#npc-2)
- [Quest Items](#quest-items)
- [Object](#object)
- [Door](#door)
- [Perl Debugging](#perl-debugging)


# Beginners Guide To Perl

* Are you new to Perl? Perl isn't just a EQEmu scripting language, it's been around for eons and used in many systems
* Here is a reference to basic Perl [Beginners Guide to Perl](http://www.tizag.com/beginnerT/)

# Real Use Examples

* Modifying NPC Stats (Example coming)
* Get Item Stats (Example coming)
* Get Spell Stats (Example coming)

# How Perl Quests Are Loaded

### NPC

In order of operations, an npc's script will be dictated by the first script that it finds below

* quests/zoneshortname/id.pl
* quests/zoneshortname/npc_name.pl
* quests/global/npcid.pl
* quests/global/npc_name.pl
* quests/zoneshortname/default.pl
* quests/global/default.pl

### Player

In order of operations, a player's script will be dictated by the first script that it finds below

* quests/zoneshortname/player_v[instance_version].pl
* quests/zoneshortname/player.pl
* quests/global/player.pl

# Global Scripts

* Global scripts were designed to run on top of the scripts mentioned above, meaning if you have a player script in a zone directory and a global player script, they will both execute and not interfere with each other

### Player

* quests/global/global_player.pl

### NPC

* quests/global/global_npc.pl

### Item

Item Scripts are quest scripts attached to Items.
Items will load a script on the first event that triggers them and will load one and only one from the following location. Which ever it finds first in the following order

* ./quests/zone/items/item_script.pl
* ./quests/global/items/item_script.pl
* ./quests/zone/items/default.pl
* ./quests/global/items/default.pl

### Spell Scripts

Spell Scripts are quest scripts attached to Spells.
Spells will load a script on the first event that triggers them and will load one and only one from the following location. Which ever it finds first in the following order:

* ./quests/zone/spells/spell_id.pl
* ./quests/global/spells/spell_id.pl
* ./quests/zone/spells/default.pl
* ./quests/global/spells/default.pl

# Perl Sub Events

A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)

| Event Name | Event Trigger |
| --- | --- |
| [EVENT_AGGRO](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_aggro) | When a mob aggros a client.
| [EVENT_AGGRO_SAY](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_aggro_say) | When a mob is targeted, the player types something, and NPC is in combat.
| [EVENT_ATTACK](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_attack) | When the NPC is attacked.
| [EVENT_AUGMENT_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_augment_item) | When a client augments an item.
| [EVENT_AUGMENT_INSERT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_augment_insert) | When a client inserts an augment into an item.
| [EVENT_AUGMENT_REMOVE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_augment_remove) | When a client removes an augment from an item.
| [EVENT_CAST](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_cast) | Triggered when a client casts a spell.
| [EVENT_CAST_BEGIN](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_cast_begin) | When a client begins to cast a spell.
| [EVENT_CAST_ON](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_cast_on) | When a player casts a spell on a player or NPC.
| [EVENT_CLICKDOOR](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_clickdoor) | When the client clicks on a door object.
| [EVENT_CLICK_OBJECT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_click_object) | When the client clicks on an object.
| [EVENT_COMBAT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_combat) | When an NPC enters or leaves combat.
| [EVENT_COMBINE_FAILURE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_combine_failure) | When a combine is unsuccessful.
| [EVENT_COMBINE_SUCCESS](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_combine_success) | When a combine is successful.
| [EVENT_COMMAND](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_command) | When a player says anything like a command. 
| [EVENT_CONNECT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_connect) | When a player connects to the world.
| [EVENT_DEATH](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_death) | When the NPC dies. Fires before death finishes.
| [EVENT_DEATH_COMPLETE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_death_complete) | When the NPC dies.
| [EVENT_DESTROY_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_destroy_item) | When a client destroys an item.
| [EVENT_DISCONNECT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_disconnect) | When a player disconnects from the world.
| [EVENT_DISCOVER_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_discover_item) | When an item is discovered.
| [EVENT_DROP_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_drop_item) | When a client drops an item.
| [EVENT_DUEL_LOSE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_duel_lose) | When a client loses a duel.
| [EVENT_DUEL_WIN](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_duel_win) | When a client wins a duel.
| [EVENT_ENTER](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_enter) | When a client enters a mob's proximity.
| [EVENT_ENTER_AREA](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_enter_area) | When a client enters the area of a mob.
| [EVENT_ENTERZONE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_enterzone) | When a player enters the zone.
| [EVENT_EQUIP_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_equip_item) | When a player equips an item.
| [EVENT_EXIT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_exit) | When a client leaves a mob's proximity.
| [EVENT_FEIGN_DEATH](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_feign_death) | When a client feign death.
| [EVENT_FISH_FAILURE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_fish_failure) | When a client fails at fishing.
| [EVENT_FISH_START](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_fish_start) | When a client starts fishing.
| [EVENT_FISH_SUCCESS](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_fish_success) | When a client succeeds at fishing.
| [EVENT_FORAGE_FAILURE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_forage_failure) | When a client fails at foraging.
| [EVENT_FORAGE_SUCCESS](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_forage_success) | When a client succeeds at foraging.
| [EVENT_GROUP_CHANGE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_group_change) | When a group change occurs.
| [EVENT_HATE_LIST](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_hate_list) | When a mob's hate list is changed.
| [EVENT_HP](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_hp) | When a mob's HP drops below a threshold.
| [EVENT_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_item) | When an item or money is turned into the mob.
| [EVENT_ITEM_CLICK](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_item_click) | When an item is clicked.
| [EVENT_ITEM_CLICK_CAST](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_item_click_cast) | When a client casts the click effect on an item.
| [EVENT_ITEM_ENTER_ZONE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_item_enter_zone) | Called when an item that would trigger EVENT_SCALE_CALC is in the inventory when a player zones in.
| [EVENT_ITEM_TICK](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_item_tick) | When the click effect of an item ticks.
| [EVENT_KILLED_MERIT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_killed_merit) | When an NPC dies and the client is in a group credited with doing the most damage.
| [EVENT_LEAVE_AREA](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_leave_area) | When a client leaves a mob's area.
| [EVENT_LEVEL_UP](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_level_up) | When the player gains a level.
| [EVENT_LOOT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_loot) | When a player successfully loots an item from a corpse.
| [EVENT_NPC_SLAY](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_npc_slay) | When an NPC slays another NPC.
| [EVENT_PLAYER_PICKUP](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_player_pickup) | When a player picks up an object from the ground.
| [EVENT_POPUPRESPONSE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_popupresponse) | When a player clicks a button on a popup.
| [EVENT_PROXIMITY_SAY](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_proximity_say) | When a client enters a mob's proximity and uses an appropriate text trigger.
| [EVENT_RESPAWN](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_respawn) | Triggered on respawn.
| [EVENT_SAY](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_say) | When a mob is targeted and the player types something.
| [EVENT_SCALE_CALC](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_scale_calc) | When an item is equipped.
| [EVENT_SIGNAL](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_signal) | When a signal is received.
| [EVENT_SLAY](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_slay) | Whenever an NPC kills a player.
| [EVENT_SPAWN](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spawn) | When the NPC spawns.
| [EVENT_SPELL_EFFECT_CLIENT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_client) | When the spell lands on a client.
| [EVENT_SPELL_EFFECT_NPC](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_npc) | When the spell lands on an NPC.
| [EVENT_SPELL_BUFF_TIC_CLIENT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_buff_tic_client) | When the spell ticks on a client.
| [EVENT_SPELL_BUFF_TIC_NPC](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_buff_tic_npc) | When the spell ticks on an NPC.
| [EVENT_SPELL_EFFECT_TRANSLOCATE_COMPLETE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_translocate_complete) | When translocation is complete.
| [EVENT_SPELL_FADE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_fade) | When a spell fades.
| [EVENT_TARGET_CHANGE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_target_change) | When a mob changes their current target or clears it.
| [EVENT_TASKACCEPTED](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_taskaccepted) | When a player accepts a task from the task selector window.
| [EVENT_TASK_COMPLETE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_task_complete) | When a player completes a task.
| [EVENT_TASK_FAIL](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_task_fail) | When a player fails a task.
| [EVENT_TASK_STAGE_COMPLETE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_task_stage_complete) | When a task stage is completed.
| [EVENT_TASK_UPDATE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_task_update) | When a player's task is updated.
| [EVENT_TIMER](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_timer) | When the duration of a timer elapses.
| [EVENT_TRADE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_trade) | When a client begins a trade.
| [EVENT_UNAUGMENT_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_unaugment_item) | When a client removes an augment from an item.
| [EVENT_UNEQUIP_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_unequip_item) | When a client unequips an item.
| [EVENT_WAYPOINT_ARRIVE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_waypoint_arrive) | When a mob arrives at a waypoint.
| [EVENT_WAYPOINT_DEPART](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_waypoint_depart) | When a mob leaves a waypoint.
| [EVENT_WEAPON_PROC](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_weapon_proc) | When a weapon procs.
| [EVENT_ZONE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_zone) | When a player zones.

## Text Response Example

All speaking responses are included in a **$text** variable

```perl
if ($text=~/hail/i) # Note the /i. This means it is case-insensitive. It is always better to include this.
if ($text=~/Hello/) # Would match "Hello", but not "hello".
if ($text=~/hello/) # Would match "hello", but not "Hello".
if ($text=~/hello/i) # Would match "Hello" and "hello".
if ($text=~/me/) # Would match the "me" in "name", but not the "me" in "NAME".
if ($text=~/\bme\b/) # Would not match the "me" in "name" or the "me" in "NAME". The "\b" means there must not be text next to the match so "me" must be by itself.
if ($text=~/^me$/i) # Would only match if "me" is the only text said. The "^" tells what must be the first thing said and the "$" tells what must be the last thing.
```

## Special Text Response Examples

These responses allow you to check for multiple strings within your text variable.

```perl
if ($text=~/Hail|Hi|Hello/i) # Will check if the text contains "Hail", "Hi", or "Hello".
if ($text!~/Hail|Hi|Hello/i) # Will check if the text does not contain "Hail", "Hi", or "Hello".
```

# Exported Variables

* A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)
* Exported variables are sometimes available globally during sub-events, some exported variables are only available in certain sub-events

```perl
$activity_id # Returns the ID of the task stage completed (in EVENT_TASK_STAGE_COMPLETE); Returns the ID of the task updated or complete (in EVENT_TASK_COMPLETE, EVENT_TASK_UPDATE)
$charid # Returns the character ID of the client that triggered the Event or a negative value if no client was involved.
$class # Returns the class of the user that triggered the event.
$caster_id # Returns the ID of the caster (in EVENT_SPELL_EFFECT_CLIENT, EVENT_SPELL_EFFECT_NPC, EVENT_SPELL_BUFF_TIC_CLIENT, EVENT_SPELL_BUFF_TIC_NPC)
$combat_state # Returns 1 for starting combat, returns 0 for leaving combat (in EVENT_COMBAT)
$corpse # Returns the ID of the corpse in which an item was looted (in EVENT_LOOT)
$donecount # Return the number of hand-ins completed [i.e. 5 of 10 Crushbone Belts, the 5 would be returned] (in EVENT_TASK_COMPLETE, EVENT_TASK_UPDATE)
$doorid # Returns ID of the door clicked (in EVENT_CLICK_DOOR)
$faction # Returns the faction level number of the user with the NPC
$fished_items # Returns the item ID of fished item (in EVENT_FISH_SUCCESS)
$foraged_item # Returns the item ID of foraged item (in EVENT_FORAGE_SUCCESS)
$grouped # Returns 0 or 1 depending on group status (in EVENT_GROUP_CHANGED)
$hate_state # Return the state of hate (in EVENT_HATE_LIST)
$hpevent # Returns the value set by quest::setnexthpevent();
$item1 # The item ID in the first slot.
$item2 # The item ID in the second slot.
$item3 # The item ID in the third slot.
$item4 # The item ID in the fourth slot.
$item1_charges # The number of charges in the first slot.
$item2_charges # The number of charges in the second slot.
$item3_charges # The number of charges in the third slot.
$item4_charges # The number of charges in the fourth slot.
$item1_attuned # The attuned setting in the first slot (1 if attuned, 0 if not attuned).
$item2_attuned # The attuned setting in the second slot (1 if attuned, 0 if not attuned).
$item3_attuned # The attuned setting in the third slot (1 if attuned, 0 if not attuned).
$item4_attuned # The attuned setting in the fourth slot (1 if attuned, 0 if not attuned).
$itemcount{itemid} # $itemcount{1001} would return 2 if the user turned in 2 1001 items.
$itemid # Return the item ID of items used (in EVENT_ITEM_CLICK_CAST, EVENT_ITEM_CLICK)
$itemname # Returns the item name of items used (in EVENT_ITEM_CLICK_CAST, EVENT_ITEM_CLICK)
$killed # Returns the NPC id of the npc slain (in EVENT_NPC_SLAY)
$killer_damage # Returns the damage of the mob's killer's killing blow (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
$killer_id # Returns the entity ID of a mob's killer (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
$killer_skill # Returns the skill ID of the mob's killer's killing blow (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
$killer_spell # Returns the spell ID of the mob's killer's spell (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
$hasitem{itemid} # Checks the character's inventory master slots for an item
$hpevent # Used to identify the HP Event set via quest::setnexthpevent() (in EVENT_HP)
$hpratio # Returns HP Ratio
$inchpevent # Used potentially for the incoming hp event or next hp event (in EVENT_HP)
$instanceid # Returns the instance ID of the current zone
$instanceversion # Returns the instance version
$langid # Returns the language id the player/npc is currently using. (in EVENT_SAY, EVENT_AGGRO_SAY, EVENT_PROXIMITY_SAY)
$looted_charges # Returns the charges of the looted item (in EVENT_LOOT)
$looted_id # Returns the ID of the looted item (in EVENT_LOOT)
$oncursor{itemid} # Checks the character's front item on the cursor for an item
$objectid # Returns the object id of the clicked item (in EVENT_CLICK_OBJECT)
$mlevel # Returns the level of the mob that the user triggered the Event on.
$mname # Returns the mob's name (returns non-clean, for a clean name use $npc->GetCleanName();).
$mobid # Returns the npc_types ID of the mob that the user triggered the Event on.
$name # Returns the name of the user that triggered the Event.
$picked_up_id # Returns the item id picked up (in EVENT_PLAYER_PICKUP)
$popupid # Returns the ID of the popup window (in EVENT_POPUPRESPONSE)
$race # Returns the race of the user that triggered the Event.
$raided # Returns 0 or 1 depending on group status (in EVENT_GROUP_CHANGED)
$recipe # Returns the ID of the recipe (in EVENT_COMBINE_SUCCESS, EVENT_COMBINE_FAILURE)
$signal # Returns the value of a signal sent using quest::signalwith() (in EVENT_SIGNAL)
$slotid # Returns the slot ID of the item used (in EVENT_ITEM_CLICK_CAST, EVENT_ITEM_CLICK)
$spell_id # Returns the ID of the spell cast (in EVENT_CAST, EVENT_CAST_ON, EVENT_CAST_BEGIN)
$status # Returns the account status of the user that triggered the Event.
$target_zone_id # Returns the ID of the zone to enter, such as in casting ports (in EVENT_ZONE)
$targetid # Returns the entity id of the NPC's current (or last) target.
$targetname # Returns the name of the NPC's current (or last) target.
$task_id # Returns the task ID of the task accepted (in EVENT_TASKACCEPTED), stage completed (in EVENT_TASK_STAGE_COMPLETE), task failed (in EVENT_TASK_FAIL), task updated or completed (in EVENT_TASK_COMPLETE, EVENT_TASK_UPDATE)
$text # The text sent by players to an NPC (in EVENT_SAY), from an NPC (in EVENT_AGGRO_SAY), spoken by player when nearby the NPC (in EVENT_PROXIMITY_SAY)
$timer # Returns the value used when creating a timer with quest::settimer() (in EVENT_TIMER)
$uguild_id # Returns the ID of the guild of the user that triggered the Event.
$uguildrank # Returns the guild rank of the user that triggered the Event.
$ulevel # Returns the level of the user that triggered the Event.
$userid # Returns the ID of the user that triggered the Event.
$version # Returns the version of the door clicked (in EVENT_CLICKDOOR)
$wp # Returns current waypoint (in EVENT_WAYPOINT_ARRIVE and EVENT_WAYPOINT_DEPART)
$zonehour # Returns the current in-game hour.
$zoneid # Returns the zone id that the Event occured in.
$zoneln # Returns the zone long name that the Event occured in.
$zonemin # Returns the current in-game minute.
$zonesn # Returns the zone short name that the Event occured in.
$zonetime # Returns the current in-game time in HHMM format.
$zoneweather # Returns current weather of zone. 0 for none, 1 for rain, 2 for snow.
 
$copper # Returns the number of copper coins given to the mob.
$silver # Returns the number of silver coins given to the mob.
$gold # Returns the number of gold coins given to the mob.
$platinum # Returns the number of platinum coins given to the mob.
 
$x # The X coordinate of the NPC.
$y # The Y coordinate of the NPC.
$z # The Z coordinate of the NPC.
$h # The heading of the NPC.
```

# General Quest API

*   A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/questmgr.cpp](https://github.com/EQEmu/Server/blob/master/zone/questmgr.cpp)

```perl
quest::AssignGroupToInstance(uint16 instance_id)
quest::AssignRaidToInstance(uint16 instance_id)
quest::AssignToInstance(uint16 instance_id)
quest::ChooseRandom(option1, option2, option3, option4, option5...[no limit])
quest::CreateInstance(string zone_name, uint16 version, uint32 duration)
quest::DestroyInstance(int id)
quest::FlagInstanceByGroupLeader(uint32 zone, uint16 version)
quest::FlagInstanceByRaidLeader(uint32 zone, uint16 version)
quest::FlyMode(uint8 mode [0-3])
quest::GetCharactersInInstance(uint16 instance_id)
quest::GetInstanceID(string zone_name, uint16 version)
quest::GetInstanceTimer()
quest::GetInstanceTimerByID(uint16 instance_id)
quest::GetSpellResistType(uint32 spell_id)
quest::GetSpellTargetType(uint32 spell_id)
quest::GetTimeSeconds()
quest::GetZoneID(string zone)
quest::GetZoneLongName(string zone)
quest::IsBeneficialSpell(uint32 spell_id)
quest::IsEffectInSpell(uint32 spell_id, uint32 effect_id)
quest::IsRunning()
quest::LearnRecipe(int recipe_id)
quest::MerchantCountItem(uint32 npc_id, uint32 item_id)
quest::MerchantSetItem(uint32 npc_id, uint32 item_id, [uint32 quantity])
quest::ModifyNPCStat(string key, string value)
quest::MovePCInstance(int zone_id, int instance_id, float x, float y, float z, [float heading])
quest::RemoveAllFromInstance(uint16 instance_id)
quest::RemoveFromInstance(uint16 instance_id)
quest::SendMail(stirng to, string from, string subject, string message)
quest::SetRunning(bool is_running)
quest::UpdateInstanceTimer(int16 instance_id, uint32 duration)
quest::UpdateSpawnTimer(uint32 spawn2_id, uint32 updated_time_till_repop)
quest::UpdateZoneHeader(string key, string value)
quest::activespeakactivity(int task_id)
quest::activespeaktask()
quest::activetasksinset(int task_set)
quest::addldonloss(int losses, int theme_id)
quest::addldonpoints(int points, int theme_id)
quest::addldonwin(int wins, int theme_id)
quest::addloot(uint32 item_id, uint16 charges = 0, [bool equip_item = true])
quest::addskill(int skill_id, int value)
quest::assigntask(int task_id, [bool enforce_level_requirement = false])
quest::attack(string client_name)
quest::attacknpc(int npc_entity_id)
quest::attacknpctype(int npc_type_id)
quest::buryplayercorpse(int character_id)
quest::castspell(int spell_id, int target_id)
quest::changedeity(int deity_id)
quest::checktitle(int title_set_id)
quest::clear_npctype_cache(int npc_type_id)
quest::clear_proximity()
quest::clear_zone_flag(uint32 zone_id)
quest::clearspawntimers()
quest::collectitems(int item_id, [bool remove_item = true])
quest::completedtasksinset(int task_set)
quest::createBot(string first_name, string last_name, int level, int race_id, int class_id, int gender_id)
quest::createdoor(string model_name, float x, float y, float z, float heading, [int object_type = 58], [int size = 100])
quest::creategroundobject(int item_id, float x, float y, float z, float heading, [uint32 decay_time-ms = 300000])
quest::creategroundobjectfrommodel(string model_name, float x, float y, float z, float heading, [int object_type], [uint32 decay_time-ms = 300000])
quest::createguild(string guild_name, string leader_name)
quest::crosszonemessageplayerbyname(int channel_id, string name, string message)
quest::crosszonesetentityvariablebyclientname(string client_name, string key, string value)
quest::crosszonesetentityvariablebynpctypeid(int npc_type_id, string key, string value)
quest::crosszonesignalclientbycharid(int character_id, int value)
quest::crosszonesignalclientbycharid(int character_id, int value)
quest::crosszonesignalclientbycharid(string name, int value)
quest::crosszonesignalclientbycharid(string name, int value)
quest::crosszonesignalnpcbynpctypeid(uint32 npc_type_id, uint32 value)
quest::debug(string message, [uint8 debug_level = 1 [1-3]])
quest::delglobal(string key)
quest::depop(int npc_type_id = 0)
quest::depop_withtimer(int npc_type_id = 0)
quest::depopall(int npc_type_id = 0)
quest::depopzone([bool start_spawn_status = false])
quest::ding()
quest::disable_proximity_say()
quest::disable_spawn2(int spawn2_id)
quest::disablerecipe(int recipe_id)
quest::disabletask(int task_id, 2, 3, [up to 10])
quest::doanim(int animation_id)
quest::echo(int emote_color_id, string message)
quest::emote(string message)
quest::enable_proximity_say()
quest::enable_spawn2(int spawn2_id)
quest::enabledtaskcount(int task_set)
quest::enablerecipe(int recipe_id)
quest::enabletask(int task_id, 2, 3, [up to 10])
quest::enabletitle(int title_set_id)
quest::exp(int amount)
quest::faction(int faction_id, int value, [int temp = 0])
quest::factionvalue()
quest::failtask(int task_id)
quest::firsttaskinset(int task_set)
quest::follow(int entity_id, [int distance = 10])
quest::forcedoorclose(int door_id, [bool alt_mode = 0])
quest::forcedooropen(int door_id, [int alt_mode=0])
quest::get_spawn_condition(string zone_short, [int instance_id], int condition_id)
quest::getguildnamebyid(uint32 guild_id)
quest::getlevel(int type)
quest::getplayerburiedcorpsecount(int character_id)
quest::gettaskactivitydonecount(int task_id, int activity_id)
quest::givecash(int copper, int silver, int gold, int platinum)
quest::gmmove(float x, float y, float z)
quest::gmsay(string message, [int color_id], [bool send_to_world = 0])
quest::has_zone_flag(uint32 zone_id)
quest::incstat(int stat_id, int value)
quest::isdisctome(int item_id)
quest::isdooropen(int door_id)
quest::istaskaappropriate(int task_id)
quest::istaskactive(int task_id)
quest::istaskactivityactive(int task_id, int activity_id)
quest::istaskcompleted(int task_id)
quest::istaskenabled(int task_id)
quest::itemlink(int item_id)
quest::lasttaskinset(int task_set)
quest::level(int new_level)
quest::me(string message)
quest::movegrp(int zone_id, float x, float y, float z)
quest::movepc(int zone_id, float x, float y, float z [float heading])
quest::moveto(float x, float y, float z, [float heading], [bool save_guard_location])
quest::nexttaskinset(int task_set, int task_id)
quest::npcfeature(string feature [race|gender|texture|helm|haircolor|beardcolor|eyecolor1|eyecolor2|hair|face|beard|heritage|tatoo|details|size], int value)
quest::npcgender(int gender_id)
quest::npcrace(int race_id)
quest::npcsize(int size)
quest::npctexture(int texture_id)
quest::pause(int duration-ms)
quest::permaclass(int class_id)
quest::permagender(int gender_id)
quest::permarace(int race_id)
quest::playerfeature(string feature [race|gender|texture|helm|haircolor|beardcolor|eyecolor1|eyecolor2|hair|face|beard|heritage|tatoo|details|size], int setting)
quest::playergender(int gender_id)
quest::playerrace(int race_id)
quest::playersize(int newsize)
quest::playertexture(int texture_id)
quest::popup(string window_title, string message, int popup_id, int buttons, int duration)
quest::pvp(string mode [on|off])
quest::qs_player_event(int character_id, string message)
quest::qs_send_query(string query)
quest::rain(int weather)
quest::rebind(int zone_id, float x, float y, float z)
quest::removetitle(int title_set_id)
quest::repopzone()
quest::resettaskactivity(int task_id, int activity_id)
quest::respawn(int npc_type_id, int grid_id)
quest::resume()
quest::safemove()
quest::save()
quest::say(string message, int language_id])
quest::saylink(string message, [bool silent = false], [link_name = message])
quest::scribespells(int max_level, [int min_level = 1])
quest::selfcast(int spell_id)
quest::set_proximity(float min_x, float max_x, float min_y, float max_y, [float min_z], [float max_z], [say])
quest::set_zone_flag(uint32 zone_id)
quest::setallskill(int value)
quest::setanim(int npc_type_id, int appearance_number[0-4])
quest::setglobal(stirng key, string value, int options, string duration)
quest::setguild(int guild_id, int guild_rank_id)
quest::sethp(int mob_health_percentage [0-100])
quest::setlanguage(int skill_id, int value)
quest::setnexthpevent(int at_mob_percentage)
quest::setnextinchpevent(int at_mob_percentage)
quest::setskill(int skill_id, int value)
quest::setsky(uint8 sky)
quest::setstat(stat_id, int_value)
quest::settarget(string target_enum ['npc_type', 'entity'], int target_id)
quest::settime(int new_hour, int new_min, [bool update_world = true])
quest::settimer(string timer_name, int seconds)
quest::settimerMS(string timer_name, int milliseconds)
quest::sfollow()
quest::shout(string message)
quest::shout2(string message)
quest::showgrid(int grid_id)
quest::signal(int npc_id, [int wait_ms])
quest::signalwith(int npc_id, int signal_id, [int wait_ms])
quest::snow(int weather)
quest::spawn(int npc_type_id, int grid_id, int int_unused, float x, float y, float z)
quest::spawn2(int npc_type_id, int grid_id, int int_unused, float x, float y, float z, float heading)
quest::spawn_condition(string zone_short, [int instance_id], uint16 condition_id, int16 value)
quest::spawn_from_spawn2(int spawn2_id)
quest::start(int waypoint)
quest::stop()
quest::stopalltimers()
quest::stoptimer(string timer_name)
quest::summonallplayercorpses(int char_id, float dest_x, float dest_y, float dest_z, float dest_heading)
quest::summonburiedplayercorpse(uint32 char_id, float dest_x, float dest_y, float dest_z, float dest_heading)
quest::summonitem(int item_id, [int charges])
quest::surname(string name)
quest::targlobal(stirng key, string value, string duration, int npc_id, int chararacter_id, int zone_id)
quest::task_setselector(int task_set_id)
quest::taskexplorearea(int explore_id)
quest::taskselector(int task_id, 2, 3, 4, 5 [up to 40])
quest::tasktimeleft(int task_id)
quest::toggle_spawn_event(uint32 event_id, [bool is_enabled = false], [bool is_strict = false], [bool reset_base = false])
quest::toggledoorstate(int door_id)
quest::traindisc(int tome_item_id)
quest::traindiscs(int max_level, [int min_level = 1])
quest::unique_spawn(int npc_type_id, int grid_id, int int_unused, float x, float y, float z, [float heading])
quest::unscribespells()
quest::untraindiscs()
quest::updatetaskactivity(int task_id, int activity_id, [int count], [bool ignore_quest_update = false])
quest::varlink(uint32 item_id)
quest::voicetell(string client_name, int macro_id, int ace_id, int gender_id)
quest::we(int emote_color_id, string message)
quest::wearchange(uint8 slot, uint16 texture_id, [uint32 hero_forge_model_id = 0], [uint32 elite_material_id = 0])
quest::worldwidemarquee(uint32 color_id, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, string message)
quest::write(string file_name, string message)
quest::ze(int emote_color_id, string message)
quest::zone(string zone_name)
```

### **Conditionals**

**Syntax**

```perl
if($variable1 [operator] $variable2) {
    quest::commands;
}
```

**Example:**

```perl
if($variable1 [operator] $variable2) {
    quest::commands;
}
elsif($variable1 [someotheroperator] $variable2) {
    quest::commands;
}
else {
    quest::commands;
}
```

Note, special operators apply to string comparisons in Perl!

**Operators:**

```perl
$1 == $2 # If variable $1 is the same as variable $2, carry on.
$1 != $2 # If variable $1 is NOT the same as variable $2, carry on.
$1 > $2 # If variable $1 is greater than variable $2, carry on.
$1 < $2 # If variable $1 is less than variable $2, carry on.
$1 >= $2 # If variable $1 is greater than or equal to variable $2, carry on.
$1 <= $2 # If variable $1 is less than or equal to variable $2, carry on.
$1 eq $2 # If string variable $1 is the same as string variable $2, carry on.
$1 ne $2 # If string variable $1 is NOT the same as string variable $2, carry on.
$1 =~ $2 # If string variable $1 contains/matches the string variable $2, carry on.
```

In this example, if the user is a smaller level than the mob the mob says "I'm a higher level than you!"

```perl
if($ulevel < $mlevel) {
	quest::say("I'm a higher level than you!");
}
if($name ne "Joe") {
	quest::say("I will only talk to joe!");
}
```

##### **Using $npc->GetHateList();**

```perl
sub EVENT_AGGRO_SAY {
    if($text=~/hate/i) {
        my @hatelist = $npc->GetHateList();
        foreach $ent (@hatelist) {
            my $h_ent = $ent->GetEnt();  # do not forget GetEnt() or the script halts!
            my $h_dmg = $ent->GetDamage();
            my $h_hate = $ent->GetHate();
            if($h_ent) {
                my $h_ent_name = $h_ent->GetCleanName();
                quest::say("$h_ent_name is on my hate list with $h_hate hate and $h_dmg damage.");
            }
        }
    }
}
```

#### **Function Lists**

*   Nearly every function for Perl can be found in the EQEmu source[https://github.com/EQEmu/Server/blob/master/zone/perl_mob.cpp](https://github.com/EQEmu/Server/blob/master/zone/perl_mob.cpp) 

# Client

```perl
$client->AccountID()
$client->AccountName()
$client->AddAAPoints(uint32 points)
$client->AddAlternateCurrencyValue(uint32 currency_id, int32 amount)
$client->AddCrystals(uint32 radiant_count, uint32 ebon_count)
$client->AddEXP(uint32 experience_points)
$client->AddLevelBasedExp(uint8 exp_percentage, uint8 max_level = 0)
$client->AddMoneyToPP(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, bool update_client)
$client->AddPVPPoints(uint32 points)
$client->AddSkill(int skill_id, uint16 value)
$client->Admin()
$client->AssignTask(int task_id, int npc_id, [bool enforce_level_requirement = false])
$client->AssignToInstance(uint16 instance_id)
$client->AutoSplitEnabled()
$client->BreakInvis()
$client->CalcPriceMod(mob*, [bool reverse = false])
$client->CanHaveSkill(int skill_id)
$client->ChangeLastName(string last_name)
$client->CharacterID()
$client->CheckIncreaseSkill(int skill_id, int chance_modifier = 0)
$client->CheckSpecializeIncrease(uint16 spell_id)
$client->ClearCompassMark()
$client->ClearZoneFlag(uint32 zone_id)
$client->Connected()
$client->DecreaseByID(uint32 type, unit8 amount)
$client->DeleteItemInInventory(int16 slot_id, [int8 quantity = 0], [bool client_update = false])
$client->Disconnect()
$client->DropItem(int16 slot_id)
$client->Duck()
$client->Escape()
$client->ExpeditionMessage(int expedition_id, string message)
$client->FailTask(int task_id)
$client->ForageItem()
$client->GMKill()
$client->GetAAExp()
$client->GetAALevel(uint32 aa_skill_id)
$client->GetAAPercent()
$client->GetAAPoints()
$client->GetAccountFlag(string flag)
$client->GetAggroCount()
$client->GetAllMoney()
$client->GetAnon()
$client->GetAugmentAt(uint32 slot, uint32 aug_slot)
$client->GetAugmentIDAt(int16 slot_id, int16 aug_slot)
$client->GetBaseAGI()
$client->GetBaseCHA()
$client->GetBaseDEX()
$client->GetBaseFace()
$client->GetBaseINT()
$client->GetBaseSTA()
$client->GetBaseSTR()
$client->GetBaseWIS()
$client->GetBecomeNPCLevel()
$client->GetBindHeading(int index = 0)
$client->GetBindX(int index = 0)
$client->GetBindY(int index = 0)
$client->GetBindZ(int index = 0)
$client->GetBindZoneID(int index = 0)
$client->GetCarriedMoney()
$client->GetCharacterFactionLevel(int32 faction_id)
$client->GetClientVersion()
$client->GetClientVersionBit()
$client->GetCorpseCount()
$client->GetCorpseID(uint8 corpse)
$client->GetCorpseItemAt(uint32 corpse_id, uint16 slot_id)
$client->GetCustomItemData(int16 slot_id, string identifier)
$client->GetDiscSlotBySpellID(int32 spell_id)
$client->GetDuelTarget()
$client->GetEXP()
$client->GetEbonCrystals()
$client->GetEndurance()
$client->GetEnduranceRatio()
$client->GetFace()
$client->GetFactionLevel(uint32 character_id, uint32 npc_id, uint32 player_race_id, uint32 player_class_id, uint32 player_deity_id, uint32 player_faction_id, mob*)
$client->GetFeigned()
$client->GetFreeSpellBookSlot(uint32 start_slot = 0)
$client->GetGM()
$client->GetGroup()
$client->GetGroupPoints()
$client->GetHorseId()
$client->GetHunger()
$client->GetIP()
$client->GetInstanceID()
$client->GetInstrumentMod(uint16 spell_id)
$client->GetItemAt(uint32 slot)
$client->GetItemIDAt(int16 slot_id)
$client->GetItemInInventory(int16 slot_id)
$client->GetLDoNLosses()
$client->GetLDoNLossesTheme(int32 theme)
$client->GetLDoNPointsTheme(int32 theme)
$client->GetLDoNWins()
$client->GetLDoNWinsTheme(int32 theme)
$client->GetLanguageSkill(uint16 lanuage_id)
$client->GetLastName()
$client->GetMaxEndurance()
$client->GetModCharacterFactionLevel(int32 faction_id)
$client->GetPVP()
$client->GetPVPPoints()
$client->GetRadiantCrystals()
$client->GetRaid()
$client->GetRaidPoints()
$client->GetRawItemAC()
$client->GetRawSkill(int skill_id)
$client->GetSkill(uint16 skill_id)
$client->GetSkillPoints()
$client->GetSpellBookSlotBySpellID(uint32 spell_id)
$client->GetSpentAA()
$client->GetStartZone()
$client->GetTargetRingX()
$client->GetTargetRingY()
$client->GetTargetRingZ()
$client->GetTaskActivityDoneCount(int task_id, int activity_id)
$client->GetThirst()
$client->GetTotalSecondsPlayed()
$client->GetWeight()
$client->GoFish()
$client->GrantAlternateAdvancementAbility(int aa_id, int points, [bool ignore_cost = false])
$client->GuildID()
$client->GuildRank()
$client->HasSkill(int skill_id)
$client->HasSpellScribed(int spell_id)
$client->HasZoneFlag(uint32 zone_id)
$client->Hungry()
$client->InZone()
$client->IncStats(uint8 type, uint16 increase_val)
$client->IncreaseLanguageSkill(int skill_id, int value = 1)
$client->IncreaseSkill(int skill_id, int value = 1)
$client->IncrementAA(uint32 aa_skill_id)
$client->IsBecomeNPC()
$client->IsDueling()
$client->IsGrouped()
$client->IsLD()
$client->IsMedding()
$client->IsRaidGrouped()
$client->IsSitting()
$client->IsTaskActive(int task_id)
$client->IsTaskActivityActive(int task_id, int activity_id)
$client->IsTaskCompleted(int task_id)
$client->KeyRingAdd(uint32 item_id)
$client->KeyRingCheck(uint32 item_id)
$client->Kick()
$client->LearnRecipe(uint32 recipe_id)
$client->LeaveGroup()
$client->LoadZoneFlags()
$client->MarkCompassLoc(float x, float y, float z)
$client->MaxSkill(uint16 skill_id, uint16 class_id, uint16 level)
$client->MemSpell(uint16 spell_id, int slot, [bool update_client = true])
$client->MovePC(uint32 zone_id, float x, float y, float z, float heading)
$client->MovePCInstance(uint32 zone_id, uint32 instance_id, float x, float y, float z, float heading)
$client->NPCSpawn(npc*, string option, uint32 respawn_time=1200)
$client->NukeItem(uint32 item_id, [uint8 slot_to_check])
$client->OpenLFGuildWindow()
$client->PlayMP3(string file_name)
$client->QuestReward(int32 mob, int32 copper, int32 silver, int32 gold, int32 platinum, int32 item_id, int32 exp, [bool faction = false])
$client->ReadBook(char* book_test, uint8 type)
$client->RefundAA()
$client->RemoveFromInstance(uint16 instance_id)
$client->RemoveNoRent()
$client->ResetAA()
$client->ResetTrade()
$client->Save(uint8 commit_now)
$client->SaveBackup()
$client->ScribeSpell(uint16 spell_id, int slot, [bool update_client = true])
$client->SendColoredText(uint32 color, string message)
$client->SendFullPopup(string title, string text, uint32 popup_id, uint32 negative_id, uint32 buttons, uint32 duration, string button_name_0, string button_name_1, uint32 sound_controls)
$client->SendMarqueeMessage(uint32 type, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, std::string msg)
$client->SendMarqueeMessage(uint32 type, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, string msg)
$client->SendOPTranslocateConfirm(mob* caster, int32 spell_id)
$client->SendSound()
$client->SendTargetCommand(int32 entity_id)
$client->SendWebLink(string website_url)
$client->SendZoneFlagInfo(client* to)
$client->SetAAPoints(uint32 points)
$client->SetAATitle(string text, [bool save = false])
$client->SetAccountFlag(string flag, string value)
$client->SetBaseClass(uint32 class_id)
$client->SetBaseGender(uint32 gender_id)
$client->SetBaseRace(uint32 race_id)
$client->SetBecomeNPC(flag)
$client->SetBecomeNPCLevel(level)
$client->SetBindPoint(int to_zone = -1, int to_instance = 0, float new_x = 0.0f, float new_y = 0.0f, float new_z = 0.0f)
$client->SetCustomItemData(int16 slot_id, string identifier, string value)
$client->SetDeity(uint32 deity_id)
$client->SetDuelTarget(set_id)
$client->SetDueling(duel)
$client->SetEXP(uint32 experience_points, uint32 aa_experience_points, [bool resexp=false])
$client->SetEndurance(endurance)
$client->SetFactionLevel(uint32 character_id, uint32 npc_id, uint8 character_class, uint8 character_race, uint8 character_deity)
$client->SetFactionLevel2(uint32 character_id, int32 faction_id, uint8 character_class, uint8 character_race, uint8 character_deity, int32 value, uint8 temp)
$client->SetFeigned(in_feigned)
$client->SetGM(bool toggle)
$client->SetHorseId(horseid_in)
$client->SetHunger(in_hunger)
$client->SetHunger(int32 hunger_amount, int32 thirst_amount)
$client->SetLanguageSkill(int language_id, int value)
$client->SetMaterial(int16 slot_id, uint32 item_id)
$client->SetPVP(bool toggle)
$client->SetSkill(int skill_id, uint16 value)
$client->SetSkillPoints(inp)
$client->SetStartZone(uint32 zone_id, [float x = 0], [float y = 0], [float z = 0])
$client->SetStats(uint8 type, uint16 increase_val)
$client->SetThirst(int32 in_thirst)
$client->SetTint(int16 slot_id, uint32 color)
$client->SetTitleSuffix(string text, [bool save = false])
$client->SetZoneFlag(uint32 zone_id)
$client->SignalClient(uint32 data)
$client->SilentMessage(string message)
$client->SlotConvert2(uint8 slot)
$client->Stand()
$client->SummonItem(uint32 item_id, [int16 charges = -1], [bool attune = false], [uint32 aug1 = 0], [uint32 aug2 = 0], [uint32 aug3 = 0], [uint32 aug4 = 0], [uint32 aug5 = 0], [uint16 slot_id = 30])
$client->TGB()
$client->TakeMoneyFromPP(uint32 copper, bool update_client = false)
$client->Thirsty()
$client->TrainDiscBySpellID(int32 spell_id)
$client->Undye()
$client->UnmemSpell(int slot, [bool update_client = true])
$client->UnmemSpellAll([bool update_client = true])
$client->UnmemSpellBySpellID(int32 spell_id)
$client->UnscribeSpell(int slot, [bool update_client = true])
$client->UnscribeSpellAll([bool update_client = true])
$client->UntrainDisc(int slot, [bool update_client = true])
$client->UntrainDiscAll([update_client = true])
$client->UpdateAdmin(bool from_db = true)
$client->UpdateGroupAAs(int32 points, uint32 type)
$client->UpdateLDoNPoints(int32 points, uint32 theme)
$client->UpdateTaskActivity(int task_id, int activity_id, int count, [bool ignore_quest_update = false])
$client->UpdateWho(uint8 remove = 0)
$client->UseDiscipline(int32 spell_id, int32 target)
$client->WorldKick()
```

# Corpse

```perl
$corpse->AddItem(uint32 item_id, uint16 charges, [unt16 slot = 0])
$corpse->AddLooter(mob* who)
$corpse->AllowMobLoot(mob* them, uint8 slot)
$corpse->CanMobLoot(int character_id)
$corpse->CastRezz(uint16 spell_id, [mob* caster = nullptr])
$corpse->CompleteRezz()
$corpse->CountItems()
$corpse->Delete()
$corpse->GetCharID()
$corpse->GetCopper()
$corpse->GetDBID()
$corpse->GetDecayTime()
$corpse->GetGold()
$corpse->GetOwnerName()
$corpse->GetPlatinum()
$corpse->GetSilver()
$corpse->GetWornItem(equipslot)
$corpse->IsEmpty()
$corpse->IsLocked()
$corpse->IsRezzed()
$corpse->Lock()
$corpse->RemoveCash()
$corpse->RemoveItem(uint16 loot_slot)
$corpse->ResetLooter()
$corpse->SetCash(uint16 copper, uint16 silver, uint16 gold, uint16 platinum)
$corpse->SetDecayTimer(uint32 decay_time)
$corpse->Summon(client* client, bool is_spell)
$corpse->UnLock()
```

# EntityList 

```perl
$entity_list->CanAddHateForMob(mob* target)
$entity_list->Clear()
$entity_list->ClearClientPetitionQueue()
$entity_list->ClearFeignAggro(mob* target)
$entity_list->DeleteNPCCorpses()
$entity_list->DeletePlayerCorpses()
$entity_list->DoubleAggro(*mob target)
$entity_list->Fighting(mob* target)
$entity_list->FindDoor(uint32 door_id)
$entity_list->GetClientByAccID(uint32 account_id)
$entity_list->GetClientByCharID(uint32 character_id)
$entity_list->GetClientByID(uint16 client_id)
$entity_list->GetClientByName(name)
$entity_list->GetClientByWID(uint32 wid)
$entity_list->GetClientList()
$entity_list->GetCorpseByID(id)
$entity_list->GetCorpseByName(name)
$entity_list->GetCorpseByOwner(client)
$entity_list->GetCorpseList()
$entity_list->GetDoorsByDBID(uint32 database_id)
$entity_list->GetDoorsByDoorID(uint32 door_id)
$entity_list->GetDoorsByID(uint32 entity_id)
$entity_list->GetDoorsList()
$entity_list->GetGroupByClient(client* client)
$entity_list->GetGroupByID(id)
$entity_list->GetGroupByLeaderName(leader)
$entity_list->GetGroupByMob(mob* mob)
$entity_list->GetMob(name)
$entity_list->GetMobByID(id)
$entity_list->GetMobByNpcTypeID(get_id)
$entity_list->GetMobID(id)
$entity_list->GetMobList()
$entity_list->GetNPCByID(id)
$entity_list->GetNPCByNPCTypeID(npc_id)
$entity_list->GetNPCList()
$entity_list->GetObjectByDBID(uint32 database_id)
$entity_list->GetObjectByID(uint32 entity_id)
$entity_list->GetObjectList()
$entity_list->GetRaidByClient(client)
$entity_list->GetRaidByID(id)
$entity_list->GetRandomClient(float x, float y, float z, float distance, [client* exclude_client = nullptr])
$entity_list->HalveAggro(mob* target)
$entity_list->MakeNameUnique(string name)
$entity_list->Message(uint32 guild_id, uint32 emote_color_type, string message)
$entity_list->MessageClose(mob* sender, bool skip_sender, float distance, uint32 emote_color_type, string message)
$entity_list->MessageGroup(mob* sender, bool skip_close, uint32 emote_color_type, string message)
$entity_list->MessageStatus(uint32 guild_id, uint32 emote_color_type, string message)
$entity_list->OpenDoorsNear(npc* opener)
$entity_list->RemoveAllClients()
$entity_list->RemoveAllCorpses()
$entity_list->RemoveAllDoors()
$entity_list->RemoveAllGroups()
$entity_list->RemoveAllMobs()
$entity_list->RemoveAllNPCs()
$entity_list->RemoveAllObjects()
$entity_list->RemoveAllTraps()
$entity_list->RemoveClient(delete_id)
$entity_list->RemoveCorpse(delete_id)
$entity_list->RemoveDoor(delete_id)
$entity_list->RemoveEntity(uint16 id)
$entity_list->RemoveFromHateLists(mob* mob, [bool set_to_one = false])
$entity_list->RemoveFromTargets(mob* target)
$entity_list->RemoveGroup(delete_id)
$entity_list->RemoveMob(delete_id)
$entity_list->RemoveNPC(delete_id)
$entity_list->RemoveObject(delete_id)
$entity_list->RemoveTrap(delete_id)
$entity_list->ReplaceWithTarget(mob* old_mob, mob* new_target)
$entity_list->SignalAllClients(uint32 data)
$entity_list->SignalMobsByNPCID(uint32 npc_type_id, int signal_id)
$entity_list->ValidMobByNpcTypeID(get_id)
```

# Group 

 * $group needs to be fetched from an entity object, for example:  $group = $client->GetGroup())

```perl
$group->CastGroupSpell(mob* caster, uint16 spell_id)
$group->DisbandGroup()
$group->GetHighestLevel()
$group->GetID()
$group->GetLeader()
$group->GetLeaderName()
$group->GetMember(int group_index)
$group->GetTotalGroupDamage(mob* other)
$group->GroupCount()
$group->GroupMessage(mob* sender, uint8 language, string message)
$group->IsGroupMember(client)
$group->IsLeader(mob* target)
$group->SendHPPacketsFrom(mob* new_member)
$group->SendHPPacketsTo(mob* new_member)
$group->SetLeader(mob* new_leader)
$group->SplitExp(uint32 exp, mob* other)
$group->SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum)
```

# Raid

```perl
$raid->Object();
```

* $raid needs to be fetched from an entity object, for example: $raid = $client->GetRaid())

```perl
$raid->BalanceHP(int32 penalty, uint32 group_id)
$raid->CastGroupSpell(mob* caster, uint16 spell_id, uint32 group_id)
$raid->GetClientByIndex(uint16 raid_indez)
$raid->GetGroup(string name)
$raid->GetHighestLevel()
$raid->GetID()
$raid->GetLowestLevel()
$raid->GetMember(int raid_index)
$raid->GetTotalRaidDamage([mob* other = nullptr])
$raid->GroupCount(uint32 group_id)
$raid->IsGroupLeader(string name)
$raid->IsLeader(string name)
$raid->IsRaidMember(string name)
$raid->RaidCount()
$raid->SplitExp(uint32 experience, [mob* other = nullptr])
$raid->SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum)
$raid->TeleportGroup(mob* sender, uint32 zone_id, float x, float y, float z, float heading, uint32 group_id)
$raid->TeleportRaid(mob* sender, uint32 zone_id, float x, float y, float z, float heading)
```

# Mob

* Important Note! Most of the $mob objects also work when used with $client

```perl
$mob->AddFeignMemory(client* attacker)
$mob->BehindMob(mob* other = 0, [float x = 0.0f], [float y= 0.0f])
$mob->BuffFadeAll()
$mob->BuffFadeByEffect(int effect_id, int skip_slot = -1)
$mob->BuffFadeBySlot(int slot, bool recalc_bonuses = true)
$mob->BuffFadeBySpellID(uint16 spell_id)
$mob->CalculateDistance(float x, float y, float z)
$mob->CalculateHeadingToTarget(float x, float y)
$mob->CanClassEquipItem(uint32 item_id)
$mob->CanThisClassDodge()
$mob->CanThisClassDoubleAttack()
$mob->CanThisClassDualWield()
$mob->CanThisClassParry()
$mob->CanThisClassRiposte()
$mob->CastToClient()
$mob->CastToCorpse()
$mob->CastToMob()
$mob->CastToNPC()
$mob->CastingSpellID()
$mob->ChangeSize(float in_size, [bool no_restriction = false])
$mob->Charmed()
$mob->CheckAggro(mob* other)
$mob->CheckAggroAmount(uint16 spell_id)
$mob->CheckHealAggroAmount(uint16 spell_id, uint32 possible_heal_amt)
$mob->CheckLoS(mob*)
$mob->CheckLoSToLoc(float x, float y, float z, float mob_size)
$mob->ClearFeignMemory()
$mob->ClearSpecialAbilities()
$mob->CombatRange(mob* target)
$mob->Depop(startspawntimer = true)
$mob->DivineAura()
$mob->DoAnim(int animation_number, [int type = 0])
$mob->DoKnockback(mob* caster, uint32 push_back_amount, uint32 push_up_amount)
$mob->DontBuffMeBefore()
$mob->DontDotMeBefore()
$mob->DontHealMeBefore()
$mob->DontRootMeBefore()
$mob->DontSnareMeBefore()
$mob->DoubleAggro(mob* other)
$mob->Emote(string message)
$mob->EntityVariableExists(string id)
$mob->FaceTarget([mob* target = 0])
$mob->FindBuff(uint16 spell_id)
$mob->FindGroundZ(float x, float y, float z_offset)
$mob->FindType(uint8 type, [bool offensive = false], [uint16 threshold = 100])
$mob->GMMove(float x, float y, float z, [float heading = 0.01])
$mob->Gate()
$mob->GetAA(uint32 rank_id)
$mob->GetAAByAAID(uint32 aa_id)
$mob->GetAC()
$mob->GetAGI()
$mob->GetATK()
$mob->GetActSpellCasttime(uint16 spell_id, uint32 cast_time)
$mob->GetActSpellCost(uint16 spell_id, int32 cost)
$mob->GetActSpellDamage(uint16 spell_id, int32 value)
$mob->GetActSpellDuration(uint16 spell_id, int32 duration)
$mob->GetActSpellHealing(uint16 spell_id, int32 value)
$mob->GetActSpellRange(uint16 spell_id, float range)
$mob->GetAggroRange()
$mob->GetAllowBeneficial()
$mob->GetAppearance()
$mob->GetArmorTint(uint8 material_slot)
$mob->GetAssistRange()
$mob->GetBaseGender()
$mob->GetBaseRace()
$mob->GetBaseSize()
$mob->GetBeard()
$mob->GetBeardColor()
$mob->GetBodyType()
$mob->GetBuffSlotFromType(uint16 type)
$mob->GetCHA()
$mob->GetCR()
$mob->GetCasterLevel(spell_id)
$mob->GetClass()
$mob->GetClassLevelFactor()
$mob->GetCleanName()
$mob->GetCorruption()
$mob->GetDEX()
$mob->GetDR()
$mob->GetDamageAmount(mob* target_mob)
$mob->GetDeity()
$mob->GetDrakkinDetails()
$mob->GetDrakkinHeritage()
$mob->GetDrakkinTattoo()
$mob->GetEntityVariable(string id)
$mob->GetEquipment(uint8 material_slot)
$mob->GetEquipmentColor(uint8 material_slot)
$mob->GetEquipmentMaterial(uint8 material_slot)
$mob->GetEyeColor1()
$mob->GetEyeColor2()
$mob->GetFR()
$mob->GetFlurryChance()
$mob->GetFollowID()
$mob->GetGender()
$mob->GetHP()
$mob->GetHPRatio()
$mob->GetHairColor()
$mob->GetHairStyle()
$mob->GetHandToHandDamage()
$mob->GetHandToHandDelay()
$mob->GetHaste()
$mob->GetHateAmount(mob* mob, [bool is_damage = false])
$mob->GetHateDamageTop(mob* other)
$mob->GetHateList()
$mob->GetHateRandom()
$mob->GetHateTop()
$mob->GetHeading()
$mob->GetHelmTexture()
$mob->GetHerosForgeModel(uint8 material_slot)
$mob->GetID()
$mob->GetINT()
$mob->GetInvul()
$mob->GetItemHPBonuses()
$mob->GetItemStat(uint32 item_id, string stat)
$mob->GetLevel()
$mob->GetLevelCon(uint8 other_level)
$mob->GetLevelHP(uint8 level)
$mob->GetLuclinFace()
$mob->GetMR()
$mob->GetMana()
$mob->GetManaRatio()
$mob->GetMaxAGI()
$mob->GetMaxCHA()
$mob->GetMaxDEX()
$mob->GetMaxHP()
$mob->GetMaxINT()
$mob->GetMaxMana()
$mob->GetMaxSTA()
$mob->GetMaxSTR()
$mob->GetMaxWIS()
$mob->GetMeleeMitigation()
$mob->GetModSkillDmgTaken(int skill_id)
$mob->GetModVulnerability(uint8 resist)
$mob->GetNPCTypeID()
$mob->GetName()
$mob->GetNimbusEffect1()
$mob->GetNimbusEffect2()
$mob->GetNimbusEffect3()
$mob->GetOwnerID()
$mob->GetPR()
$mob->GetPetID()
$mob->GetPetOrder()
$mob->GetPetType()
$mob->GetPhR()
$mob->GetRace()
$mob->GetResist(type)
$mob->GetReverseFactionCon(iother)
$mob->GetRunAnimSpeed()
$mob->GetRunspeed()
$mob->GetSTA()
$mob->GetSTR()
$mob->GetShieldTarget()
$mob->GetSize()
$mob->GetSkill(int skill_id)
$mob->GetSkillDmgTaken(int skill_id)
$mob->GetSpecialAbility(int special_ability)
$mob->GetSpecialAbilityParam(int special_ability, int param)
$mob->GetSpecializeSkillValue(uint16 spell_id)
$mob->GetSpellHPBonuses()
$mob->GetSpellIDFromSlot(slot)
$mob->GetSpellStat(uint32 spell_id, string stat, uint8 slot)
$mob->GetTarget()
$mob->GetTexture()
$mob->GetWIS()
$mob->GetWalkspeed()
$mob->GetWaypointH()
$mob->GetWaypointID()
$mob->GetWaypointPause()
$mob->GetWaypointX()
$mob->GetWaypointY()
$mob->GetWaypointZ()
$mob->GetX()
$mob->GetY()
$mob->GetZ()
$mob->GetZoneID()
$mob->GoToBind()
$mob->HalveAggro(mob* other)
$mob->HasNPCSpecialAtk(string ability_string)
$mob->HasOwner()
$mob->HasPet()
$mob->HasProcs()
$mob->HasShieldEquiped()
$mob->HasTwoHandBluntEquiped()
$mob->HasTwoHanderEquipped()
$mob->HateSummon()
$mob->Heal()
$mob->HealDamage(int32 amount, [mob* caster = 0])
$mob->InterruptSpell([uint16 spell_id = 0xffff])
$mob->IsAIControlled()
$mob->IsAmnesiad()
$mob->IsBeacon()
$mob->IsBeneficialAllowed(mob* target)
$mob->IsBlind()
$mob->IsCasting()
$mob->IsClient()
$mob->IsCorpse()
$mob->IsDoor()
$mob->IsEliteMaterialItem(uint8 material_slot)
$mob->IsEngaged()
$mob->IsEnraged()
$mob->IsFeared()
$mob->IsImmuneToSpell(uint16 spell_id, [mob* caster = nullptr])
$mob->IsInvisible([mob* other = 0])
$mob->IsMeleeDisabled()
$mob->IsMezzed()
$mob->IsMob()
$mob->IsMoving()
$mob->IsNPC()
$mob->IsNPCCorpse()
$mob->IsObject()
$mob->IsPet()
$mob->IsPlayerCorpse()
$mob->IsRoamer()
$mob->IsRooted()
$mob->IsRunning()
$mob->IsSilenced()
$mob->IsStunned()
$mob->IsTargetable()
$mob->IsTargeted()
$mob->IsTrap()
$mob->IsWarriorClass()
$mob->Kill()
$mob->MakePet(uint16 spell_id, string pet_type, [string name = nullptr])
$mob->Mesmerize()
$mob->Message(uint32 emote_color_type, string message)
$mob->ModSkillDmgTaken(int skill, int16 value)
$mob->ModVulnerability(uint8 resist, int16 value)
$mob->ProcessSpecialAbilities(string str)
$mob->RangedAttack(mob* other)
$mob->RemoveFromFeignMemory(client* attacker)
$mob->RemoveNimbusEffect(int32 effect_id)
$mob->ResistSpell(uint8 resist_type, uint16 spell_id, [mob* caster = nullptr])
$mob->RogueAssassinate(other)
$mob->Say(string message)
$mob->SeeHide()
$mob->SeeImprovedHide()
$mob->SeeInvisible()
$mob->SeeInvisibleUndead()
$mob->SendPosUpdate([uint8 send_to_self = 0])
$mob->SendPosition()
$mob->SendTo(float new_x, float new_y, float new_z)
$mob->SendToFixZ(float new_x, float new_y, float new_z)
$mob->SendWearChange(uint8 material_slot)
$mob->SetAA(int aa_id, int points, [int charges = 0])
$mob->SetAllowBeneficial(bool value)
$mob->SetAppearance(int appearance [0|1|2|3|4], [ignore_self = true])
$mob->SetBodyType(int32 type, [bool overwrite_orig = false])
$mob->SetCurrentWP(waypoint)
$mob->SetDeltas(float delta_x, float delta_y, float delta_z, float delta_h)
$mob->SetDisableMelee(bool value)
$mob->SetEntityVariable(string id, string var)
$mob->SetExtraHaste(int haste)
$mob->SetFlurryChance(uint8 value)
$mob->SetFlyMode(uint8 flymode[0|1|2|3])
$mob->SetFollowID(id)
$mob->SetGender(int32 gender)
$mob->SetHP(int32 hp)
$mob->SetHate(mob* other, [int32 hate = 0], [int32 damage = 0])
$mob->SetHeading(float heading)
$mob->SetInvisible(uint8 state)
$mob->SetInvul(bool set_invulnerable)
$mob->SetLD(bool value)
$mob->SetLevel(uint8 in_level, [bool command = false])
$mob->SetMana(amount)
$mob->SetMaxHP()
$mob->SetOOCRegen(int32 new_ooc_regen)
$mob->SetOwnerID(uint16 new_owner_id)
$mob->SetPetID(uint16 new_pet_id)
$mob->SetPetOrder(i)
$mob->SetRace(int32 race)
$mob->SetRunAnimSpeed(int8 speed)
$mob->SetRunning(bool value)
$mob->SetShieldTarget(mob)
$mob->SetSpecialAbility(int ability, int value)
$mob->SetSpecialAbilityParam(int ability, int param, int value)
$mob->SetTarget(mob)
$mob->SetTargetDestSteps(uint8 target_steps)
$mob->SetTargetable(bool targetable)
$mob->SetTexture(int32 texture)
$mob->Shout(string message)
$mob->SignalClient(client* client, uint32 data)
$mob->Spin()
$mob->StartEnrage()
$mob->Stun(int duration)
$mob->TempName(string name)
$mob->ThrowingAttack(mob* other)
$mob->TryMoveAlong(float distance, float angle, bool send)
$mob->WipeHateList()
```

# NPC

```perl
$npc->AddCash(uint16 copper, uint16 silver, uint16 gold, uint16 platinum)
$npc->AddDefensiveProc(int spell_id, int chance)
$npc->AddLootTable([uint32 loottable_id])
$npc->AddMeleeProc(int spell_id, int chance)
$npc->AddRangedProc(int spell_id, int chance)
$npc->AssignWaypoints(uint32 grid_id)
$npc->CalculateNewWaypoint()
$npc->ChangeLastName(string name)
$npc->CheckNPCFactionAlly(int32 faction_id)
$npc->ClearItemList()
$npc->ClearLastName()
$npc->CountLoot()
$npc->DisplayWaypointInfo(client* target)
$npc->DoClassAttacks(mob* target)
$npc->GetAccuracyRating()
$npc->GetAttackDelay()
$npc->GetAttackSpeed()
$npc->GetAvoidanceyRating()
$npc->GetCombatState()
$npc->GetCopper()
$npc->GetGold()
$npc->GetGrid()
$npc->GetGuardPointX()
$npc->GetGuardPointY()
$npc->GetGuardPointZ()
$npc->GetLoottableID()
$npc->GetMaxDMG()
$npc->GetMaxDamage(uint8 target_level)
$npc->GetMaxWp()
$npc->GetMinDMG()
$npc->GetNPCFactionID()
$npc->GetNPCHate(mob* entity)
$npc->GetNPCSpellsID()
$npc->GetPetSpellID()
$npc->GetPlatinum()
$npc->GetPrimSkill()
$npc->GetPrimaryFaction()
$npc->GetScore()
$npc->GetSecSkill()
$npc->GetSilver()
$npc->GetSlowMitigation()
$npc->GetSp2()
$npc->GetSpawnKillCount()
$npc->GetSpawnPointH()
$npc->GetSpawnPointID()
$npc->GetSpawnPointX()
$npc->GetSpawnPointY()
$npc->GetSpawnPointZ()
$npc->GetSpellFocusDMG()
$npc->GetSpellFocusHeal()
$npc->GetSwarmOwner()
$npc->GetSwarmTarget()
$npc->GetWaypointMax()
$npc->IsAnimal()
$npc->IsGuarding()
$npc->IsOnHatelist(mob* target)
$npc->ModifyNPCStat(string key, string value)
$npc->NextGuardPosition()
$npc->PauseWandering(int pause_time)
$npc->PickPocket(client* thief)
$npc->RemoveAISpell(int spell_id)
$npc->RemoveCash()
$npc->RemoveDefensiveProc(int spell_id)
$npc->RemoveFromHateList(mob* target)
$npc->RemoveItem(uint32 item_id, [uint16 quantity = 0], [uint16 slot_id = 0])
$npc->RemoveMeleeProc(int spell_id)
$npc->RemoveRangedProc(int spell_id)
$npc->ResumeWandering()
$npc->SaveGuardSpot([bool clear_guard_spot = false])
$npc->SetCopper(uint32 copper_amount)
$npc->SetGold(uint32 gold_amount)
$npc->SetGrid(int32 grid_id)
$npc->SetNPCFactionID(int32 faction_id)
$npc->SetPetSpellID(uint16 amount)
$npc->SetPlatinum(uint32 platinum_amount)
$npc->SetPrimSkill(int skill_id)
$npc->SetSaveWaypoint(uint16 waypoint)
$npc->SetSecSkill(int skill_id)
$npc->SetSilver(uint32 silver_amount)
$npc->SetSp2(uint32 set_spawn_group_id)
$npc->SetSpellFocusDMG(int new_spell_focus_dmg)
$npc->SetSpellFocusHeal(int32 new_spell_focus_heal)
$npc->SetSwarmTarget(int target_id)
$npc->SetTaunting(bool toggle)
$npc->SetWaypointPause()
$npc->SignalNPC(int signal_id)
$npc->StartSwarmTimer(uint32 duration)
$npc->StopWandering()
$npc->UpdateWaypoint(int wp_index)
```

# Quest Items

* Below objects require you to fetch an item instance via an item getter, for example:

```perl
$item = $client->GetItemAt(slot);
$item->GetCharges();
```

```perl
$quest_item->GetAugment(int16 slot_id)
$quest_item->GetCharges()
$quest_item->GetID()
$quest_item->GetName()
$quest_item->IsAttuned()
$quest_item->IsType(type)
$quest_item->ItemSay(string text [int language_id])
$quest_item->SetScale(float scale_multiplier)
```

# Object

* Below objects require you to fetch the object instance via an entity getter, for example:

```perl
$object = $entity_list->GetObjectByID(ID);
$object->SetLocation(x, y, z);
```

```perl
$object->ClearUser()
$object->Close()
$object->Delete([bool reset_state = false])
$object->DeleteItem(uint8 index)
$object->Depop()
$object->EntityVariableExists(string key)
$object->GetDBID()
$object->GetEntityVariable(string key)
$object->GetHeading()
$object->GetID()
$object->GetIcon()
$object->GetItemID()
$object->GetModelName()
$object->GetSize()
$object->GetSize()
$object->GetSize()
$object->GetSolidType()
$object->GetType()
$object->GetX()
$object->GetY()
$object->GetZ()
$object->IsGroundSpawn()
$object->IsObject()
$object->Repop()
$object->Save()
$object->SetEntityVariable(string key, string var)
$object->SetHeading(float heading)
$object->SetID(uint16 id)
$object->SetIcon(uint32 icon)
$object->SetItemID(uint32 item_id)
$object->SetLocation(float x, float y, float z)
$object->SetModelName(string name)
$object->SetSize(float size)
$object->SetSolidType(uint16 type)
$object->SetTiltX(float tilt_x)
$object->SetTiltY(float tilt_y)
$object->SetType(uint32 type)
$object->SetX(float x)
$object->SetY(float y)
$object->SetZ(float z)
$object->StartDecay()
$object->VarSave()
```

# Door

* Below objects require you to fetch the door instance via an entity getter, for example:

```perl
$door = $entity_list->GetDoorsByID(ID);
$door->GetModelName();
```

```perl
$door->GetDoorDBID()
$door->GetDoorID()
$door->GetHeading()
$door->GetID()
$door->GetIncline()
$door->GetIncline()
$door->GetKeyItem()
$door->GetLockpick()
$door->GetModelName()
$door->GetNoKeyring(uint8 type)
$door->GetOpenType()
$door->GetX()
$door->GetY()
$door->GetZ()
$door->InsertDoor()
$door->SetHeading(float heading)
$door->SetIncline(uint32 incline)
$door->SetKeyItem(uint32 key_item_id)
$door->SetLocation(float x, float y, float z)
$door->SetLockpick(uint32 lockpick_type)
$door->SetModelName(string name)
$door->SetNoKeyring(uint8 no_key_ring)
$door->SetOpenType(uint32 open_type)
$door->SetSize(uint32 size)
$door->SetX(float x)
$door->SetY(float y)
$door->SetZ(float z)
```

# Perl Debugging

* Run the perl file against the perl processor for syntax errors. (e.g. perl <filename.pl>)
* Reload the quest in game. #reloadquest or #rq
* See any recent API errors. #questerrors
* Peek at the zone console and see if any hints appear there. Also look at the zone logfile.