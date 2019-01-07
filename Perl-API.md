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
      - [[Inventory Slot Identifiers|Perl Inventory Slot Identifiers]]
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
| [EVENT_DEATH_ZONE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_death_zone) | When an NPC dies (used by the zone controller).
| [EVENT_DESTROY_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_destroy_item) | When a client destroys an item.
| [EVENT_DISCONNECT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_disconnect) | When a player disconnects from the world.
| [EVENT_DISCOVER_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_discover_item) | When an item is discovered.
| [EVENT_DROP_ITEM](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_drop_item) | When a client drops an item.
| [EVENT_DUEL_LOSE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_duel_lose) | When a client loses a duel.
| [EVENT_DUEL_WIN](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_duel_win) | When a client wins a duel.
| [EVENT_ENTER](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_enter) | When a client enters a mob's proximity.
| [EVENT_ENTER_AREA](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_enter_area) | When a client enters the area of a mob.
| [EVENT_ENTERZONE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_enterzone) | When a player enters the zone.
| [EVENT_ENVIRONMENTAL_DAMAGE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_environmental_damage) | When taking any sort of environmental damage.
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
| [EVENT_SPAWN_ZONE](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spawn_zone) | When the NPC spawns (used by the zone controller).
| [EVENT_SPELL_EFFECT_CLIENT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_client) | When the spell lands on a client.
| [EVENT_SPELL_EFFECT_NPC](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_npc) | When the spell lands on an NPC.
| [EVENT_SPELL_EFFECT_BUFF_TIC_CLIENT](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_buff_tic_client) | When the spell ticks on a client.
| [EVENT_SPELL_EFFECT_BUFF_TIC_NPC](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_spell_effect_buff_tic_npc) | When the spell ticks on an NPC.
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
| [EVENT_USE_SKILL](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_use_skill) | When a client uses a skill
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

| Exported Variable | Usage |
| --- | --- |
| $activity_id | Returns the ID of the task stage completed (in EVENT_TASK_STAGE_COMPLETE); Returns the ID of the task updated or complete (in EVENT_TASK_COMPLETE, EVENT_TASK_UPDATE)
| $charid | Returns the character ID of the client that triggered the Event or a negative value if no client was involved.
| $class | Returns the class of the user that triggered the event.
| $caster_id | Returns the ID of the caster (in EVENT_SPELL_EFFECT_CLIENT, EVENT_SPELL_EFFECT_NPC, EVENT_SPELL_BUFF_TIC_CLIENT, EVENT_SPELL_BUFF_TIC_NPC)
| $combat_state | Returns 1 for starting combat, returns 0 for leaving combat (in EVENT_COMBAT)
| $corpse | Returns the ID of the corpse in which an item was looted (in EVENT_LOOT)
| $donecount | Return the number of hand-ins completed [i.e. 5 of 10 Crushbone Belts, the 5 would be returned] (in EVENT_TASK_COMPLETE, EVENT_TASK_UPDATE)
| $doorid | Returns ID of the door clicked (in EVENT_CLICK_DOOR)
| $faction | Returns the faction level number of the user with the NPC
| $fished_items | Returns the item ID of fished item (in EVENT_FISH_SUCCESS)
| $foraged_item | Returns the item ID of foraged item (in EVENT_FORAGE_SUCCESS)
| $grouped | Returns 0 or 1 depending on group status (in EVENT_GROUP_CHANGED)
| $hate_state | Return the state of hate (in EVENT_HATE_LIST)
| $hpevent | Returns the value set by quest::setnexthpevent();
| $item1 | The item ID in the first slot.
| $item2 | The item ID in the second slot.
| $item3 | The item ID in the third slot.
| $item4 | The item ID in the fourth slot.
| $item1_charges | The number of charges in the first slot.
| $item2_charges | The number of charges in the second slot.
| $item3_charges | The number of charges in the third slot.
| $item4_charges | The number of charges in the fourth slot.
| $item1_attuned | The attuned setting in the first slot (1 if attuned, 0 if not attuned).
| $item2_attuned | The attuned setting in the second slot (1 if attuned, 0 if not attuned).
| $item3_attuned | The attuned setting in the third slot (1 if attuned, 0 if not attuned).
| $item4_attuned | The attuned setting in the fourth slot (1 if attuned, 0 if not attuned).
| $itemcount{itemid} | | $itemcount{1001} would return 2 if the user turned in 2 1001 items.
| $itemid | Return the item ID of items used (in EVENT_ITEM_CLICK_CAST, EVENT_ITEM_CLICK)
| $itemname | Returns the item name of items used (in EVENT_ITEM_CLICK_CAST, EVENT_ITEM_CLICK)
| $killed | Returns the NPC id of the npc slain (in EVENT_NPC_SLAY)
| $killer_damage | Returns the damage of the mob's killer's killing blow (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
| $killer_id | Returns the entity ID of a mob's killer (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
| $killer_skill | Returns the skill ID of the mob's killer's killing blow (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
| $killer_spell | Returns the spell ID of the mob's killer's spell (in EVENT_DEATH, EVENT_DEATH_COMPLETE)
| $hasitem{itemid} | Checks the character's inventory master slots for an item
| $hpevent | Used to identify the HP Event set via quest::setnexthpevent() (in EVENT_HP)
| $hpratio | Returns HP Ratio
| $inchpevent | Used potentially for the incoming hp event or next hp event (in EVENT_HP)
| $instanceid | Returns the instance ID of the current zone
| $instanceversion | Returns the instance version
| $langid | Returns the language id the player/npc is currently using. (in EVENT_SAY, EVENT_AGGRO_SAY, EVENT_PROXIMITY_SAY)
| $looted_charges | Returns the charges of the looted item (in EVENT_LOOT)
| $looted_id | Returns the ID of the looted item (in EVENT_LOOT)
| $oncursor{itemid} | Checks the character's front item on the cursor for an item
| $objectid | Returns the object id of the clicked item (in EVENT_CLICK_OBJECT)
| $mlevel | Returns the level of the mob that the user triggered the Event on.
| $mname | Returns the mob's name (returns non-clean, for a clean name use | $npc->GetCleanName();).
| $mobid | Returns the npc_types ID of the mob that the user triggered the Event on.
| $name | Returns the name of the user that triggered the Event.
| $picked_up_id | Returns the item id picked up (in EVENT_PLAYER_PICKUP)
| $popupid | Returns the ID of the popup window (in EVENT_POPUPRESPONSE)
| $race | Returns the race of the user that triggered the Event.
| $raided | Returns 0 or 1 depending on group status (in EVENT_GROUP_CHANGED)
| $recipe | Returns the ID of the recipe (in EVENT_COMBINE_SUCCESS, EVENT_COMBINE_FAILURE)
| $signal | Returns the value of a signal sent using quest::signalwith() (in EVENT_SIGNAL)
| $slotid | Returns the slot ID of the item used (in EVENT_ITEM_CLICK_CAST, EVENT_ITEM_CLICK)
| $spell_id | Returns the ID of the spell cast (in EVENT_CAST, EVENT_CAST_ON, EVENT_CAST_BEGIN)
| $status | Returns the account status of the user that triggered the Event.
| $target_zone_id | Returns the ID of the zone to enter, such as in casting ports (in EVENT_ZONE)
| $targetid | Returns the entity id of the NPC's current (or last) target.
| $targetname | Returns the name of the NPC's current (or last) target.
| $task_id | Returns the task ID of the task accepted (in EVENT_TASKACCEPTED), stage completed (in EVENT_TASK_STAGE_COMPLETE), task failed (in EVENT_TASK_FAIL), task updated or completed (in EVENT_TASK_COMPLETE, EVENT_TASK_UPDATE)
| $text | The text sent by players to an NPC (in EVENT_SAY), from an NPC (in EVENT_AGGRO_SAY), spoken by player when nearby the NPC (in EVENT_PROXIMITY_SAY)
| $timer | Returns the value used when creating a timer with quest::settimer() (in EVENT_TIMER)
| $uguild_id | Returns the ID of the guild of the user that triggered the Event.
| $uguildrank | Returns the guild rank of the user that triggered the Event.
| $ulevel | Returns the level of the user that triggered the Event.
| $userid | Returns the ID of the user that triggered the Event.
| $version | Returns the version of the door clicked (in EVENT_CLICKDOOR)
| $wp | Returns current waypoint (in EVENT_WAYPOINT_ARRIVE and EVENT_WAYPOINT_DEPART)
| $zonehour | Returns the current in-game hour.
| $zoneid | Returns the zone id that the Event occured in.
| $zoneln | Returns the zone long name that the Event occured in.
| $zonemin | Returns the current in-game minute.
| $zonesn | Returns the zone short name that the Event occured in.
| $zonetime | Returns the current in-game time in HHMM format.
| $zoneweather | Returns current weather of zone. 0 for none, 1 for rain, 2 for snow.
| $copper | Returns the number of copper coins given to the mob.
| $silver | Returns the number of silver coins given to the mob.
| $gold | Returns the number of gold coins given to the mob.
| $platinum | Returns the number of platinum coins given to the mob.
| $x | The X coordinate of the NPC.
| $y | The Y coordinate of the NPC.
| $z | The Z coordinate of the NPC.
| $h | The heading of the NPC.

# General Quest API

*   A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/questmgr.cpp](https://github.com/EQEmu/Server/blob/master/zone/questmgr.cpp)

### AssignGroupToInstance

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parmeter:** 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:** 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Assigns a group to an instance. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Create a scalar variable to store instance_id--GetInstanceID returns int
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); 
quest::AssignGroupToInstance($Instance);
```



### AssignRaidToInstance 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parmeter:** 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Assigns a raid to an instance.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Create a scalar variable to store instance_id--GetInstanceID returns int
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); 
quest::AssignRaidToInstance($Instance);
```

### AssignToInstance

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Assigns a single player to an instance.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example**
```perl
#:: Create a scalar variable to store instance_id--GetInstanceID returns int
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); 
quest::AssignToInstance($Instance);
```
### ChooseRandom

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; option1, option2, option3... 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns one of the items listed in its arguments randomly.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Choose a random reward: 1001 - Cloth Cap, 1004 - Cloth Shirt, 1011 - Cloth Pants
quest::summonitem(quest::ChooseRandom(1001, 1004, 1011);
```

### CreateInstance 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_name _(string)_, version _(uint16)_, duration _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Creates an instance in the given zone using specified version and duration.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::CreateInstance("mirb", 50, 10800);
```

### DestroyInstance 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Destroys the given instance. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::DestroyInstance(50);
```

### FlagInstanceByGroupLeader

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone _(uint32)_, version _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Assigns the group leader's instance to a player 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Zone 237 (mirb), instance 50
quest::FlagInstanceByGroupLeader(237,50);
```

### FlagInstanceByRaidLeader

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone _(uint32)_, version _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Assigns the raid leader's instance to a player

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Zone 237 (mirb), instance 50
quest::FlagInstanceByRaidLeader(237,50);
```

### FlyMode

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; mode [0-3] _(uint8)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:** 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sets flymode for player where 0 = Off, 1 = On, 2 = Levitate. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
 #:: Turn fly mode on
quest::FlyMode(1);
```

### GetCharactersInInstance

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:** 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns a hash of character id and instance id

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Instance ID 50
quest::GetCharactersInInstance(50); #:: Returns 50,123456
```

### GetInstanceID

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_name _(string)_, version _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:** 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the instance id of the given zone/verison.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example**
```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); #:: Returns uint16
quest::AssignToInstance($Instance);
```

### GetInstanceTimer

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the timer for the instance.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example**
```perl
quest::GetInstanceTimer(); #:: Returns uint32
```

### GetInstanceTimerByID

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the duration timer of the specified instance.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Note: If you do not provide an instance_id in the method it defaults to instance id 0 and returns 0 for time remaining.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example**
```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); #:: Returns uint16
quest::GetInstanceTimerByID($Instance); #:: Returns timer int
```

### GetSpellResistType

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spell_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the [Resist Type](https://github.com/EQEmu/Server/wiki/Resist-Types) of the specified spell.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example**
```perl
quest::GetSpellResistType($spell_id); #:: Returns int
```

### GetSpellTargetType

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spell_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the [Target Type](https://github.com/EQEmu/Server/wiki/Target-Types) of the specified spell.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example**
```perl
quest::GetSpellTargetType($spell_id); #:: Returns int
```

### GetTimeSeconds

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns unix time in seconds.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::GetTimeSeconds(); #:: Returns int
```

### GetZoneID

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the zone id.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::GetZoneID($zonesn); #:: Returns int
```

### GetZoneLongName

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the long name of the zone.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::GetZoneLongName($zonesn); #:: Returns string
```

### IsBeneficialSpell

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spell_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns true if the specified spell is beneficial.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::IsBeneficialSpell($spell_id); #:: Returns 0 or 1
```

### IsEffectInSpell

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spell_id _(uint32)_, effect_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns true if the specified spell has the specified [Spell Effect](https://github.com/EQEmu/Server/wiki/Spell-Effect-IDs).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Check for Spell Effect 23 - Fear
quest::IsEffectInSpell($spell_id, 23); #:: Returns 0 or 1
```

### IsRunning

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the running state--0 is walking, 1 is running.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
quest::IsRunning(); #:: Returns 0 or 1
```

### LearnRecipe

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; recipe_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Makes the client learn a recipe.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Teach recipe_id 2141 - Pickled Bixie
quest::LearnRecipe(2141);
```

### MerchantCountItem

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_id _(uint32)_, item_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the number of the specified item in stock at the specified merchant.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Find out how many 12260 - Fuzzlecutter Formula 5000 are in stock at Ping_Fuzzlecutter (9133)
quest::MerchantCountItem(9133, 12260); #:: Returns int
```

### MerchantSetItem

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_id _(uint32)_, item_id _(uint32)_, quantity _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Changes the number of the specified items in stock, at the specified quantity, at the specified merchant.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Make sure there is plenty of 12260 - Fuzzlecutter Formula 5000 in stock at Ping_Fuzzlecutter (9133)
quest::MerchantSetItem(9133, 12260, 1000); #:: Quantity 1000
```

### ModifyNPCStat

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; key _(string)_, value _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Changes the specified [npc_types](https://github.com/EQEmu/Server/wiki/npc_types) stat of the specified NPC on the fly--changes are not saved to the npc_types in the DB.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
#:: Adjust the runspeed to 1.25
quest::modifynpcstat("runspeed", 1.25);
```

### MovePCInstance

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_id _(uint32)_, instance_id _(uint32)_, x _(float)_, y _(float)_, z _(float)_, heading _(float)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Moves a player to the specified instance of the specified zone at the specified location and heading.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**
```perl
sub EVENT_CLICKDOOR {
    #:: Match door id 3: Frozen Nightmare (mirb) zone in
    if ($doorid == 3) {
        #:: Create a scalar variable to store instance_id--GetInstanceID returns int
        my $InstanceMirB = quest::GetInstanceID("mirb",50);
        #:: Match if an instance exists
        if ($InstanceMirB > 0) {
            #:: Move the player to mirb (237), to their instance, at X - 607, Y - 1503, Z - 33, Heading - 0 (north)
            quest::MovePCInstance(237,$InstanceMirB,607,1503,33,0);
        }
    }
}
```

### RemoveAllFromInstance

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Removes ALL players from an instance by instance ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_DEATH_COMPLETE {
     #:: Instance ID is a pre-exported variable
     quest::RemoveAllFromInstance($instanceid);
}
```

### RemoveFromInstance

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(uint16)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Removes the player that triggered the event from an instance by instance ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_CLICKDOOR {
     if ($doorid == 1) {
          quest::RemoveFromInstance($instanceid);
     }
}
```

### SendMail

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to _(string)_, from _(string)_, subject _(string)_, message _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to send a mail message.

### SetRunning

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; is_running _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to toggle run/walk state.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SPAWN {
	#:: Set the NPC to run
	quest::SetRunning(1);
}
```

### UpdateInstanceTimer

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; instance_id _(int16)_, duration _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to update a zone instance timer by instance id by the number of seconds specified.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_CLICKDOOR {
     #:: When they open door 7...
     if ($doorid == 7) {
          #:: Add one hour of time to the current instance
          quest::UpdateInstanceTimer($instanceid,3600);
     }
}
```

### UpdateSpawnTimer

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spawn2_id _(uint32)_, updated_time_till_repop _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to update a spawn timer by spawn2 ID and time specified in ms.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_DEATH_COMPLETE {
     #:: Set a random timer on Fippy Darkpaw's spawn point
     quest::updatespawntimer(10875,(int(rand(600))+3600)*1000);
}
```

### UpdateZoneHeader

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; key _(string)_, value _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Allows you to manipulate zone header settings on the fly.  The [Quest Manager](https://github.com/EQEmu/Server/blob/c08993b60b7b5328398459a458648a114c3fb331/zone/questmgr.cpp#L3149) lists the following possible strings: ztype, fog_red, fog_green, fog_blue, fog_minclip, fog_maxclip, gravity, time_type, rain_chance, rain_duration, snow_chance, snow_duration, sky, safe_x, safe_y, safe_z, max_z, underworld, minclip, maxclip, fog_density, suspendbuffs.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Set the max clip plane to 500 units
quest::UpdateZoneHeader("maxclip", 500);
```

### activespeakactivity

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the Activity ID of the lowest numbered active activity to speak with an NPC in the specified task.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If you have task id 150:  activity 0--kill three rats, activity 1--talk with NPC, activity 2--kill four fire beetles, activity 3--talk with NPC.

```perl
sub EVENT_SAY {
     #:: Match text for hail, case insensitive
     if ($text=~/hail/i) {
          #:: Create a scalar variable to store the current speak activity for task 150
          $speakactivity = quest::activespeakactivity(150); #:: Returns int
          #:: Match if the player is on the first speak activity
          if ($speakactivity == 1) {
               quest::say("I really hate rats.");
          }
          #:: Match if the player is on the second speak activity
          elsif ($speakactivity == 3) {
               quest::say("I really hate fire beetles.");
          }
     }
}
```

### activespeaktask

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the Task ID of the lowest numbered task slot if the player who triggered the event has an active task with an active activity to speak to the NPC (returns 0 if not).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If you have task id 150:  activity 0--kill three rats, activity 1--talk with NPC, activity 2--kill four fire beetles, activity 3--talk with NPC.

```perl
sub EVENT_SAY {
     #:: Match text for hail, case insensitive
     if ($text=~/hail/i) {
          #:: Create a scalar variable to store the current task that has a speak activity
          $speaktask = quest::activespeaktask(); #:: Returns int
          #:: Match if there's an active task with a speak activity
          if ($speaktask => 1) {
               quest::say("You have a task to speak with me and its ID is $speaktask.");
          }
          #:: Match if there's NO active task with a speak activity
          else {
               quest::say("You do not have any tasks with a speaking activity at this time.");
          }
     }
}
```

### activetasksinset

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_set _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the number of tasks in the given TaskSet that the player has active.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; You have a TaskSet "20", which consists of three tasks--200, 201, 202.

```perl
sub EVENT_SAY {
     #:: Create a scalar variable to store the number of active tasks in TaskSet 20
     $activetaskcount = quest::activetasksinset(20);  #:: returns int
     #:: Match text for hail, case insensitive
     if ($text=~/hail/i) {
          quest::say("You have $activetaskcount tasks remaining.");
     }
}
```

### addldonloss

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; losses _(int)_, theme_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Adds to loss count for LDON adventures by [LDON Theme](https://github.com/EQEmu/Server/wiki/LDON-Themes).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Add a loss for Rujarkian Hills theme
quest::addldonloss(1,4);
```

### addldonpoints

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; points _(int)_, theme_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Adds to points count for LDON adventures by [LDON Theme](https://github.com/EQEmu/Server/wiki/LDON-Themes).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Add 100 points for Rujarkian Hills theme
quest::addldonpoints(100,4);
```

### addldonwin

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; wins _(int)_, theme_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Adds to wins count for LDON adventures by [LDON Theme](https://github.com/EQEmu/Server/wiki/LDON-Themes).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Add a loss for Rujarkian Hills theme
quest::addldonwin(1,4);
```

### addloot

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; item_id _(uint32)_, charges = 0 _(uint16)_, equip_item = true _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Add an item with a number of charges to an NPC's loot (does not permanently change the loot table or lootdrop entries).  If 'equipitem' is false (0), the item will not be used by (or shown in the hands of) the NPC.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Add a 5013 - Rusty Short Sword to the NPC's loot, but do not equip the item
quest::addloot(5013,0,0);
```

### addskill

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; skill_id _(int)_, value _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sets the player's skill, by [Skill ID](https://github.com/EQEmu/Server/wiki/Skills), to the value specified.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     #:: Match text for train, case insensitive
     if ($text=~/train/i) {
          #:: Call the custom subroutine "Train"
          Train();
     }
}

#:: Custom subroutine
sub Train {
     #:: Send a message to the client in yellow (15) text
     $client->Message( 15, "Your experiences across the realm have infused you with increased power and knowledge..." );
     #:: Set all available skills to maximum for race/class at current level
     foreach my $skill (0 .. 77) {
          #:: Continue the foreach loop using the next skill ID if the client cannot use the skill ID
          next unless $client->CanHaveSkill($skill);
          #:: Create a scalar variable to store the maximum skill Value for the Skill ID
          my $maxSkill = $client->MaxSkill($skill, $client->GetClass(), $ulevel);
          #:: Continue the foreach loop using the next Skill ID if the client has a higher skill Value for the Skill ID
          next unless $maxSkill > $client->GetRawSkill($skill);
          #:: Set the Skill ID to the maximum Value that the client is allowed
          $client->SetSkill($skill, $maxSkill);
     }
     #:: Scribe all spells for current level
     quest::scribespells($ulevel);
}
```

### assigntask

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_, npcid _(int)_, enforce_level_requirement = false _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to assign a task to a client, optionally this can include the NPC ID and whether or not to enforce the level requirement specified in the DB.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Assign Task 102
quest::assigntask(102);
#:: Assign Task 103 with level requirement enforced
quest::assigntask(103, 1);
#:: Assign Task 104 and include the NPC ID
$client->AssignTask(104, $npc->GetID());
#:: Assign Task 105, include the NPC ID with level requirement enforced
$client->AssignTask(105, $npc->GetID(), 1);
```

### attack

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; client_name _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to make the NPC attack a client, by name.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     #:: Match text for "mother", case insensitive
     if ($text=~/mother/i) {
          quest::say("How dare you talk about my mother!");
          #:: Attack the client that triggered the event
          quest::attack($name);
     }
}
```

### attacknpc

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_entity_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to make the NPC attack another NPC, by Entity ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Create a scalar variable to store the Entity ID of a_large_rat
$aggromob = $entity_list->GetMobID(2011);
#:: Get him.
quest::attacknpc($aggromob);
```

### attacknpctype

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to make the NPC attack another NPC, by NPC Type ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Attack a_large_rat
quest::attacknpctype(2011);
```

### buryplayercorpse

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; character_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Buries and depops a single corpse by Character ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     #:: Create a scalar variable for storing corpse count
     my $CorpseCount = 0;
     #:: Create a scalar variable for storing the Character ID of the Client that triggered the event
     my $charid = $client->CharacterID();
     if ($text=~/hail/i) {
          #:: Send the client a message in yellow (15) text
          $client->Message(15,"I can [bury a corpse] or [destroy a corpse] that you have unburied.");
     }
     if ($text=~/bury a corpse/i) {
          #:: Match if the client character has a corpse (or corpses)
          if ($CorpseCount > 0) {
               #:: Bury the character's corpse
               quest::buryplayercorpse($charid);
               $client->Message(15,"Very well, burying one of your corpses now.");
          }
          #:: Match if the client character does not have a corpse
          else {
               $client->Message(13,"You have no unburied corpses, begone.");
          }
     }
}
```

### castspell

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spell_id _(int)_, target_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to make the NPC cast a spell, by ID, on a target, by ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Cast spell 12 - Healing, on the user that triggered the event
quest::castspell(12,$userid);
```

### changedeity

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; deity_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to permanently change the client character's deity, by [Deity ID](https://github.com/EQEmu/Server/wiki/Deity-List); kicks the client to character select.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change the client character's deity to 201 - Bertoxxulous
quest::changedeity(201);
```

### checktitle

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; title_set_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to determine if a player has the specified titleset enabled or not.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Check to see if Title Set 2 (prefix "Arbiter", suffix "Harbinger of the Old World") is enabled
quest::checktitle(2); #:: Returns bool
```

### clear_npctype_cache

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Clears the NPC Table.

### clear_proximity

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Clears an NPC's defined proximity.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SPAWN {
     #:: Create a proximity, 50 units across
     quest::set_proximity($x - 25, $x + 25, $y - 25, $y + 25);
}

sub EVENT_ENTER {
     #:: Shout a message when the event is triggered
     quest::shout("Congratulations $name, you have won the race!");
     #:: Clear the proximity since second place is the first loser
     quest::clear_proximity();
}
```

### clear_zone_flag

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to clear the Zone Flag, by ID, of a client character.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Clear the character's Zone Flag (Sleeper's Key) for 128 - The Sleeper's Tomb (sleeper)
quest::clear_zone_flag(128);
```

### clearspawntimers

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to reset the spawn timers and repop a zone--similar to #repop force.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::clearspawntimers();
```

## collectitems

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; item_id _(int)_, remove_item = true _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the number of items by ID that exist in inventory. If remove is true, items are removed as they are counted.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
	#:: Match text for "hail", case insensitive, and the client that triggered the event has a 1001 - Cloth Cap
	if ($text=~/hail/i && plugin::check_hasitem($client, 1001)) {
		quest::emote("steals your cloth cap.");
		quest::collectitems(1001, 1);
	}
}
```

## completedtasksinset

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_set _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the number of tasks in the given Task Set that the player has completed.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     #:: Match text for "tasks", case insensitive
     if ($text=~/tasks/i) {
          #:: Create a scalar variable to store the count of completed tasks in task set "200"
          my $TasksComplete = quest::completedtasksinset(200); #:: Returns int
          quest::say("You have completed $TasksComplete tasks.");
     }
}
```

## createBot

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; first_name _(string)_, last_name _(string)_, level _(int)_, race_id _(int)_, class_id _(int)_, gender_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to create a bot with the given parameters.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ENTERZONE {
     #:: Create a bot named Leroy Jenkins, who is level 50, Human, Paladin, Male
     quest::createBot("Leroy", "Jenkins", 50, 1, 3, 0);
}
```

## createdoor

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; model_name _(string)_, x _(float)_, y _(float)_, z _(float)_, heading _(float)_, object_type = 58 _(int)_, size = 100 _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Creates a new door, with type 58 and size 100 as the defaults.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::createdoor("POKTELE500", -582.532, 2324.96, -47.8143, 120, 58, 100);
```

## creategroundobject

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; item_id _(int)_, x _(float)_, y _(float)_, z _(float)_, heading _(float)_, decay_time _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Creates an object on the ground with the given parameters, decay time is ms = 300000 by default.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_WAYPOINT_ARRIVE {
     #:: Create a 12274 - Chalice of Conquest at the NPC's current location
     quest::creategroundobject(12274, $x, $y, $z, $h);
}
```

## creategroundobjectfrommodel

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; model_name _(string)_, x _(float)_, y _(float)_, z _(float)_, heading _(float)_, object_type _(int)_, decay_time _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Creates an object on the ground with the given parameters, decay time is ms = 300000 by default.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Create a 17330 - Bag of Supplies at the given location
quest::creategroundobjectfrommodel("IT64_ACTORDEF", 2497, -557, -327, 58, 17330);
```

## createguild

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; guild_name _(string)_, leader_name _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Creates a guild.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY{
     if (quest::createguild("Akkadius Fire", $client->GetName())) {
          $client->Message(15, "Guild has been created successfully");
     }
     else{
          $client->Message(15, "Guild creation error");
     }
}
```

## crosszonemessageplayerbyname

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; channel_id _(int)_, name _(string)_, message _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sends a message to a client character on the specified channel.  Useful for Expeditions and Shared Tasks.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::crosszonemessageplayerbyname(15, $name, "Hi.");
```

## crosszonesetentityvariablebyclientname

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; client_name _(string)_, key _(string)_, value _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sets entity variables world-wide for the provided client character.

## crosszonesetentityvariablebynpctypeid

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(int)_, key _(string)_, value _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sets entity variables world wide with specified npctype_id.

## crosszonesignalclientbycharid

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; character_id _(int)_, value _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Signals the client by character ID world wide.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Signal the client character who triggered the event with "5000"
quest::crosszonesignalclientbycharid($charid,5000);
```

## crosszonesignalnpcbynpctypeid

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(uint32)_, value _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Signals all NPC entities world-wide with the specified value.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Signal all 4036 - a_giant_rat with "99"
quest::crosszonesignalnpcbynpctypeid(4036, 99);
```

## debug

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; message _(string)_, debug_level _(uint8)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Allows you to export debug information for an event, at the specified level (1 through 3).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ENVIRONMENTAL_DAMAGE {
     quest::debug("EVENT_ENVIRONMENTAL_DAMAGE");
     quest::debug("env_damage is " . $env_damage);
     quest::debug("env_damage_type is " . $env_damage_type);
     quest::debug("env_final_damage is " . $env_final_damage);
}
```

## delglobal

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; key _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Deletes a quest global.  Please consider using [Data Buckets](https://github.com/EQEmu/Server/wiki/Data-Buckets) instead of quest globals.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::delglobal("strongbox");
```

## depop

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Depops an NPC by npc_type_id, default is 0 (self).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Depop self
quest::depop();
```

## depop_withtimer

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Depops an NPC by npc_type_id, default is 0 (self), and restarts the spawn point timer.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Depop self and restart spawn timer
quest::depop_withtimer();
```

## depopall

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; npc_type_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Depops all NPC entities with npc_type_id in the zone.  Default is 0 (self and others like me).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Depop all 4036 - a_giant_rat
quest::depopall(4036);
```

## depopzone

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; start_spawn_status _(bool)_ 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Depops the zone with the specified parameter.  Default is false (don't start spawn timers).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Depop the zone and don't start the spawn timers
quest::depopzone();
```

## ding

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Plays the beautiful ding sound, the trumpet fanfare for your glorious deeds.  Congratulations, winner.  You did it.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Ding!
quest::ding();
```

## disable_proximity_say

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Disables proximity say for the NPC.  Proximity say must be enabled with quest::set_proximity(); and quest::enable_proximity_say();.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::disable_proximity_say();
```

## disable_spawn2

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spawn2_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Disables the spawn point specified and depops any NPC entity from that spawn point.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Disable the spawn point for 151562 - spawngroup ID 113004 - npcIDs 15138 (Droon) and 15160 (Proon)
quest::disable_spawn2(151562);
```

## disablerecipe

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; recipe_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Disables the recipe specified by Recipe ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Disable recipe 1 - Blessed Fishing Rod
quest::disablerecipe(1);
```

## disabletask

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Disables a task so that it is not available to a client character.  Useful if you do not want someone to repeat a task.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Match if the player has an active task
if ($task != 0) {
     #:: Create a scalar variable to store the active speak-to activity
     $activity = quest::activespeakactivity($task);
     #:: Mark the activity as complete
     quest::updatetaskactivity($task, $activity);
     quest::say("Well done!");
     #:: Offer the next task, if there is one
     if (!quest::istaskactive($task)) {
          #:: Disable the task so that it cannot be repeated
          quest::disabletask($task);
          #:: Match if there are tasks remaining in the Task Set
          if ($task != quest::lasttaskinset(200)) {
               quest::say("Well done, I have another task if you are willing.");
               #:: Enable the next Task in the Task Set
               quest::enabletask(quest::nexttaskinset(200, $task));
          }
          #:: Match if there are no tasks remaining in the task set
          else {
               quest::say("Thank you for cleansing Qeynos Hills!");
          }
     }
}
```

## doanim

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; animation_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Makes the NPC perform the indicated [Animation](https://github.com/EQEmu/Server/wiki/Animations).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Perform the Cheer animation
quest::doanim(27);
```

quest::echo

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; emote_color_id _(int)_, message _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Echoes the specified message string, in the specified color, to the client console.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Echo a message in yellow text (15)
quest::echo(15,"Hello, world");
```

## emote

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; message _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Makes the NPC emote the specified message string.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_DEATH_COMPLETE {
     quest::emote("'s corpse says 'How...did...ugh...'");
}
```

## enable_proximity_say

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enables proximity say for the NPC--the target would not have to have the NPC targeted to interact if the NPC has a defined proximity and proximity say is enabled.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SPAWN {
     #:: Set the proximity bounds around the NPC on spawn, 30 units across
     $x = $npc->GetX();
     $y = $npc->GetY();
     quest::set_proximity($x-15,$x+15,$y-15,$y+15);
     quest::enable_proximity_say();
}

sub EVENT_PROXIMITY_SAY {
     if ($text=~/Ganelorn Oast/i) {
          quest::say("Ganelorn Oast! For he has single-handedly caught more poachers than any other ranger. He is credited for helping numerous endangered species recover from certain extinction. I suppose I am lucky he is fond of my sister, as I am soon to train under him as an apprentice. Perhaps one day I will even [" . quest::saylink("call upon the flames") . "] in the way that he does.");
     }
     elsif ($text=~/call upon the flames/i) {
          quest::say("Aye, Ganelorn is renowned not only for his abilities as an archer and a master of melee combat, but also for his use of powerful magics. Never before have I seen a forester evoke a fireball of such great force. It would be any ranger's dream to become his pupil just to study that one spell. Ganelorn doesn't train just anyone, though. If you want to learn from him, I'm certain you would have to prove yourself as a forester.");
     }
     if ($text=~/I want to learn/i) {
          quest::say("He is a very busy individual. I believe he is currently in the eastern part of the Karanas trying to track down a poacher. Even if you can track him down, don't get your hopes up.");
          #:: Send a signal 2 to The Greater Faydark >> Lily_Ashwood (54086)
          quest::signalwith(54086, 2, 3);
     }
}
```

## enable_spawn2

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; spawn2_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enables the specified spawn point.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_DEATH_COMPLETE {
     #:: Enable the spawn timer for 151562 - spawngroup ID 113004 - npcIDs 15138 (Droon) and 15160 (Proon)
     quest::enable_spawn2(151562);
}
```

## enabledtaskcount

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_set _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Counts the enabled tasks in the specified Task Set.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Match if there are no enabled tasks in Task Set 10
if (quest::enabledtaskcount(10) == 0) {
     quest::enabletask(50, 51, 52);
}
```

## enablerecipe

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; recipe_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enables the recipe specified by Recipe ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Enable recipe 1 - Blessed Fishing Rod
quest::enablerecipe(1);
```

## enabletask

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enables a task.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Match if the player has an active task
if ($task != 0) {
     #:: Create a scalar variable to store the active speak-to activity
     $activity = quest::activespeakactivity($task);
     #:: Mark the activity as complete
     quest::updatetaskactivity($task, $activity);
     quest::say("Well done!");
     #:: Offer the next task, if there is one
     if (!quest::istaskactive($task)) {
          #:: Disable the task so that it cannot be repeated
          quest::disabletask($task);
          #:: Match if there are tasks remaining in the Task Set
          if ($task != quest::lasttaskinset(200)) {
               quest::say("Well done, I have another task if you are willing.");
               #:: Enable the next Task in the Task Set
               quest::enabletask(quest::nexttaskinset(200, $task));
          }
          #:: Match if there are no tasks remaining in the task set
          else {
               quest::say("Thank you for cleansing Qeynos Hills!");
          }
     }
}
```

## enabletitle

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; title_set_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enables the specified Title Set.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ITEM_CLICK {
     #:: Match if item 98471 - Mastering Tinkering Master I is clicked
     if ($itemid == 98471) {
          #:: Tinkering Mastery AA ID 575 Rank 1
          $client->GrantAlternateAdvancementAbility(575,1,0);
          #:: Send a message in Yellow (15) text
          $client->Message(15,"You have mastered tinkering!");
          #:: Ding!
          quest::ding();
          #:: Enable tinkering mastery title set
          quest::enabletitle(10);
     } 
}
```

## exp

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; amount _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Gives the amount of [experience](https://github.com/EQEmu/Server/wiki/Experience-by-Level) specified to the client character.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Grant 100 experience points
quest::exp(100);
```

## faction

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; faction_id _(int)_, value _(int)_, temp _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Gives the client character the faction, specified by Faction ID, in the amount specified by value.  Temp is optional, and defaults to 0.  Temp values are:  0 (permanent, with a message), 1 (temporary, without a message), 2 (temporary, with a message), or 3 (permanent, without a message).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Set faction
quest::faction(192,10); 	#:: +10 League of Antonican Bards
quest::faction(184,10); 	#:: +10 Knights of Truth
quest::faction(135,10); 	#:: +10 Guards of Qeynos
quest::faction(273,-30); 	#:: -30 Ring of Scale
```

## factionvalue

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns faction values for the client character that triggered the event.  Generally the opposite values of $faction, with 1 being "scowls" and 9 being "ally" ($faction considers 1 to be "ally", and 9 "scowls").

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     if ($text=~/hail/i) {     
          #:: Create a scalar variable for storing faction
          my $backwardfaction = quest::factionvalue();  #:: Returns int
          quest::say("Your faction is $faction, but your faction is $backwardfaction");  #:: $faction is pre-exported and returns int
     }
}
```

## failtask

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Fails the task, by Task ID, for the client character that triggered the event.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Fail Task 216
quest::failtask(216);
```

## firsttaskinset

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_set _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the first task in the specified Task Set.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     #:: If the player hasn't completed the last task in the Task Set
     if (!quest::istaskcompleted(quest::lasttaskinset(200))) {
          #:: If the player has no tasks enabled for this task set, enable the first one
          if (quest::enabledtaskcount(200) == 0) {
               quest::say("You have not done any of my tasks before!");
               #:: Enable the first task in Task Set 200
               quest::enabletask(quest::firsttaskinset(200));
          }
     }
}
```

## follow

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; entity_id _(int)_, distance _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to make an NPC follow another NPC, specified by Entity ID.  The distance determines how many units the NPC will follow behind the specified NPC, with a default value of 10; distance is optional.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SPAWN {
     #:: Create a timer that triggers every 10 seconds
     quest::settimer("follow",10);
}

sub EVENT_TIMER {
     #:: Match if the timer is named "follow"
     if ($timer eq "follow") {
          #:: Create a scalar variable to store the NPC Type ID for mob 2161
          my $getmobbynpctype = $entity_list->GetMobByNpcTypeID(2161);
          #:: Create a scalar variable to store the Entity ID of the aforementioned NPC
          my $follow_target = $getmobbynpctype->GetID();
          #:: Follow the NPC at a default distance of 10 units
          quest::follow($follow_target);
          #:: Clean up and stop the timer
          quest::stoptimer("follow");
     }
}
```

## forcedoorclose

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; door_id _(int)_, alt_mode _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Forces a door, by Door ID, to close.  Alt_Mode is default false.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Close Door ID 31 in Befallen
quest::forcedoorclose(31);
```

## forcedooropen

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; door_id _(int)_, alt_mode _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Forces a door, by Door ID, to open.  Alt_Mode is default false.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Open Door ID 31 in Befallen
quest::forcedooropen(31);
```

## get_spawn_condition

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_short _(string)_, instance_id _(int)_, condition_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the value of the specified spawn condition.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Get the Spawn Condition for Condition ID 1, in the default instance of Lesser Faydark
quest::get_spawn_condition("lfaydark", 0, 1);  #:: Returns int
```

## getguildnamebyid

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; guild_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the name of the Guild for the specified Guild ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_CONNECT {
     #:: Announce the name of the client character that triggered the event in GM Say
     quest::gmsay("$name has connected.", 18, 1);
     #:: Announce the Account Name of the client character that triggered the event in GM Say
     quest::gmsay(" Account Name: " . $client->AccountName() . " - Status: $status", 18, 1);
     #:: Match if the client character has a guild
     if ($uguild_id > 0) {
          #:: Create a scalar variable to store the name of the client character's guild
          my $guildname = quest::getguildnamebyid($uguild_id);
          #:: Announce the client character's information in GM Say
          quest::gmsay("(Character Profile: Level $ulevel $race $class) <$guildname>)", 18, 1);
     }
     #:: Match if the client character does not have a guild
     else {
          #:: Announce the client character's information in GM Say
          quest::gmsay("(Character Profile: Level $ulevel $race $class) <No Guild>", 18, 1);
     }
}
```

## getinventoryslotid

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; identifier _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the Inventory Slot ID for the specified identifier.  Reference [Perl Inventory Slot Identifiers](https://github.com/EQEmu/Server/wiki/Perl-Inventory-Slot-Identifiers) for appropriate identifier tokens.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Create a scalar variable to store an item ID
my $charmitem = $client->GetItemIDAt(quest::getinventoryslotid("charm"));  #:: returns int
```

## getlevel

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; type _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the level for the Type specified.  Types can be 0 (self), 1 (group average), 2 (raid average), 3 (raid average, group average, or self), or 4 (self level 2--the highest level attained by self).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Get the level of the client character
quest::getlevel(0);  #:: Returns int
```

## getplayerburiedcorpsecount

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; character_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the number of corpses for the specified Character ID that are buried.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Get the number of burried corpses for character ID 12345
quest::getplayerburriedcorpsecount(12345); #:: return int
```

## gettaskactivitydonecount

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_, activity_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the task activity done count, by Task ID and Activity ID, for the client entity.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Find out how many times the client character has killed 10 beetles in Unrest
quest::gettaskactivitydonecount(15,3);  #:: Returns int
```

## givecash

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; copper _(int)_, silver _(int)_, gold _(int)_, platinum _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Gives the specified amount of money to the client that triggered the event.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Create a hash for storing cash - 20 to 100cp
my %cash = plugin::RandomCash(20,100);
#:: Grant a random cash reward
quest::givecash($cash{copper},$cash{silver},$cash{gold},$cash{platinum});
```

## gmmove

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x _(float)_, y _(float)_, z _(float)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Moves the entity to the specified coordinates.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SPAWN {
     #:: Create a timer that loops each second
     quest::settimer("position",1);
}

sub EVENT_TIMER {
     #:: Create a scalar variable to store the X position of the NPC
     my $x = $npc->GetX();
     #:: Create a scalar variable to store the Y position of the NPC
     my $y = $npc->GetY();
     #:: Match if the timer "position" has looped and the X and Y coordinates are outside the specified range
     if ($timer eq "position" && ($x < -353 || $x > -109 || $y < -549 || $y > -310)) {
          quest::shout("No! I must not leave the time chamber! If I do, I'll age and die!");
          #:: Move the NPC back to the chamber
          $npc->GMMove(-231.464005,-432.937469,202.375946,.125);
     }
}

sub EVENT_DEATH_COMPLETE {
     quest::stoptimer("position");
}
```

## gmsay

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; message _(string)_, color_id _(int)_, send_to_world _(bool)_, guild_id _(uint32)_, minstatus _()_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sends a message to the client console if the parameters are met.  [Color](https://github.com/EQEmu/Server/wiki/Emote-Colors), Send to World, Guild ID, and Minimum Status are all optional, but Color defaults to 0 (white), Send to World defaults to 0 (false), and Minimum Status defaults to 80.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Send white text to all players in the current zone with an admin status of >= 80
quest::gmsay("Text");
#:: Send yellow (15) text to all players in the current zone with an admin status of >= 80
quest::gmsay("Text", 15);
#:: Send yellow (15) text to all players with an admin status of >= 80 in all zones
quest::gmsay("Text", 15, 1);
#:: Send yellow (15) text to all players with an admin status of >= 80 in all zones, who are in a guild with a Guild ID of 30
quest::gmsay("Text", 15, 1, 30);
#:: Send yellow (15) text to all players with an admin status of >= 0 in all zones, who are in a guild with a Guild ID of 30
quest::gmsay("Text", 15, 1, 30, 0);
```

## has_zone_flag

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_id _(uint32)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to verify that a client character has the required zone flag for the specified zone.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_CLICKDOOR {
     if ($doorid == 12) {
          if (quest::has_zone_flag(200) != 1) {  #:: Returns bool
               quest::set_zone_flag(200);
          }
     }
}
```

## incstat

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; stat_id _(int)_, value _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Increases the specified stat by double the specified value.  Stat IDs: STR = 0, STA = 1, AGI = 2, DEX = 3, INT = 4, WIS = 5, CHA = 6. Note: if you're increasing stats, the client will have to zone to see the effect.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Increase STR by 20
quest::incstat(0, 10);
``` 

## isdisctome

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; item_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to check if the specified item, by Item ID, is a discipline tome.  You likely have a plugin for this (plugin::try_tome_handins).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ITEM {
     quest::traindisc($item1) if (quest::isdisctome($item1));
     quest::traindisc($item2) if (quest::isdisctome($item2));
     quest::traindisc($item3) if (quest::isdisctome($item3));
     quest::traindisc($item4) if (quest::isdisctome($item4));
}
```

## isdooropen

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; door_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Checks to see if the specified door is open.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_CLICKDOOR {
     my $doorcheck = quest::isdooropen(41);  #:: Returns bool
     if ($doorid == 41 && $doorcheck == 0) {
          quest::forcedooropen(41);
     }
}
```

## istaskaappropriate

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to see if a task is set for the appropriate level for the client character who initiated the event.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Check if task 200 is appropriate
quest::istaskaappropriate(200);  #:: Returns bool
```

## istaskactive

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to determine if a task is active, by Task ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Check if task 212 is active
quest::istaskactive(212); #:: Returns bool
```

## istaskactivityactive

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id _(int)_, activity_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to determine if a task activity is active, by Task ID and Activity ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Check if Activity 9 of Task 212 is active 
quest::istaskactivityactive(212, 9); #:: Returns bool
```

## istaskcompleted

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id (int)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to determine if a task is completed, by Task ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Check if task 212 is completed
quest::istaskcompleted(212); #:: Returns bool
```

## istaskenabled

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_id (int)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to determine if a task is enabled, by Task ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Check if task 212 is enabled
quest::istaskenabled(212); #:: Returns bool
```

## itemlink

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; item_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to send a link of the specified item, by Item ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Send an item link for a 1001 - Cloth Cap
quest::itemlink(1001);
```

## lasttaskinset

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_set _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the last task in the specified Task Set.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Find the Task ID of the last task in Task Set 200
quest::lasttaskinset(200); #:: Returns int
```

## level

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; new_level _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sets the level to the specified new level for the client character that triggered the event.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     if ($text=~/level/i) {
          #:: Match if user's level is 20 or under
          if ($ulevel <= 20) {
               #:: Give the player one more level
               quest::level($ulevel+1);
          }
          elsif ($ulevel >= 21) {
               $npc->CastSpell(808, $userid);
               quest::say("Begone!");
          }
     }
}
```

## me

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; message _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sends an emote without a name.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::me("This creature has no need for your money.");
```

## movegrp

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_id _(int)_, x _(float)_, y _(float)_, z _(float)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Moves the group of the client character that triggered the event to the specified Zone, by Zone ID, to the location specified.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Match text for "we are ready", case insensitive
if ($text=~/We are ready/i) {
     #:: Move the group to The Plane of Nightmares (ponightmare) at X=1194, Y=1121, Z=208
     quest::movegrp(204,1194,1121,280); 
}
```

## movepc

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_id _(int)_, x _(float)_, y _(float)_, z _(float)_, heading _(float)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Moves the client character that triggered the event to the specified zone, by Zone ID, at the specified location.  Heading is optional, but will default to 0 (North).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Match text for "travel to butcherblock", case insensitive
if ($text=~/travel to butcherblock/i) {
     #:: Move the character to Butcherblock Mountains (butcher), at X=3168.92, Y=851.92, Z=11.66--the Southern dock
     quest::movepc(68,3168.92,851.92,11.66);
}
```

## moveto

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x _(float)_, y _(float)_, z _(float)_, heading _(float)_, save_guard_location _(bool)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to move the NPC to the specified location.  Heading and Save Guard Location are optional.  Heading will default to 0 (North), and Save Guard Location will also default to 0, causing the NPC to path back.  Set Save Guard Location to 1 to make the NPC stay at the moveto location.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ITEM {
     #:: Match a 12278 - Abandoned Orc Shovel
     if (plugin::takeItems(12278 => 1)) {
          #:: 0=Stand, 1=Sit, 2=Duck, 3=Feign Death, 4=Kneel
          $npc->SetAppearance(0);
          #:: Move to the specified location and guard 
          quest::moveto(-395.87, 807.04, 70.53, 0, 1);
     }
     #:: Return unused items
     plugin::returnUnusedItems();
}
```

## nexttaskinset

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; task_set _(int)_, task_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Returns the next task in the specified Task Set that comes after the specified Task ID.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_SAY {
     #:: Create a scalar variable to store a task integer
     $task = quest::activespeaktask();
     #:: Match if there is an active task to speak to the NPC
     if ($task != 0) {
          #:: Match if there are no active tasks for the current speaking task
          if (!quest::istaskactive($task)) {
               #:: Disable the current speaking task
               quest::disabletask($task);
               #:: Match if the current speaking task is NOT the last task in the Task Set
               if ($task != quest::lasttaskinset(200)) {
                    quest::say("Well done, I have another task if you are willing.");
                    #:: Enable the next task in Task Set 200
                    quest::enabletask(quest::nexttaskinset(200, $task));
               }
               else {
                    quest::say("Thank you for cleansing Qeynos Hills!");
               }
          }
     }
}
```

## npcfeature
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; feature _(string)_, value _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Allows you to temporarily change the specified feature on the NPC to the specified value.  Allowable features are:  race, gender, texture, helm, haircolor, beardcolor, eyecolor1, eyecolor2, hair, face, beard, heritage, tatoo, details, and size.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change the NPC's size to 10
quest::npcfeature("size", 10);
```

## npcgender

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; gender_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to temporarily change the gender of the NPC as specified:  0 = Male, 1 = Female, 2 = Neuter.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change the NPC's gender to female
quest::npcgender(1);
```

## npcrace

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; race_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to temporarily change an NPC's [Race](https://github.com/EQEmu/Server/wiki/Race-Types).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change the NPC's Race to Golem (17)
quest::npcrace(17);
```

## npcsize

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; size _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to temporarily change the NPC's size.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change the NPC's size to 17
quest::npcsize(17);
```

## npctexture

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; texture_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to temporarily change the NPC's texture.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change the NPC's texture to 2
quest::npctexture(2);
```

## pause

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; duration-ms _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Forces the NPC to pause for the specified duration in ms.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Pause for 1 second
quest::pause(1000);
```

## permaclass

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; class_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Permanently changes the class of the client character that triggered the event to the specified class, and disconnects them.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change class to Warrior
quest::permaclass(1);
```

## permagender

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; gender_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Permanently changes the gender of the client character that triggered the event to the specified gender, and disconnects them.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change gender 0 = Male, 1 = Female, 2 = Neuter.
quest::permagender(0);
```

## permarace

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; race_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Permanently changes the [Race Type](https://github.com/EQEmu/Server/wiki/Race-Types) of the client character that triggered the event to the specified race, and disconnects them.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change race to Human
quest::permarace(1);
```

## playerfeature

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; feature _(string)_, setting _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Temporarily changes the player feature to the specified setting.  Acceptable strings are:  race, gender, texture, helm, haircolor, beardcolor, eyecolor1, eyecolor2, hair, face, beard, heritage, tattoo, details, or size.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change race to Human
quest::playerfeature("race", 1);
```

## playergender

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; gender_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Temporarily changes the gender of the client character that triggered the event to the specified gender.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change gender 0 = Male, 1 = Female, 2 = Neuter.
quest::playergender(0);
```

## playerrace

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; race_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Temporarily changes the [Race Type](https://github.com/EQEmu/Server/wiki/Race-Types) of the client character that triggered the event to the specified race.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change race to Human
quest::playerrace(1);
```

## playersize

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; newsize _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Temporarily adjusts the size of the client character that triggered the event to the specified size.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change size to 10
quest::playersize(10);
```

## playertexture

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; texture_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Temporarily changes the texture of the client character that triggered the event to the specified texture.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change texture to 2
quest::playertexture(2);
```

## popup

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; window_title _(string)_, message _(string)_, popup_id _(int)_, buttons _(int)_, duration _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Used to create a popup window with the specified parameters. The parameters popup_id, buttons, and duration are optional.  Button parameters are:  0=OK button, 1=Yes/No buttons.  Setting duration to 0 results in a popup that will remain until dismissed.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ENTER {
     #:: Popup window entitled "Teleport", Question: "Teleport to The Plane of Hate?", popup ID 666, Yes/No buttons, remain until dismissed
     quest::popup('Teleport', 'Teleport to The Plane of Hate?', 666, 1, 0);
}

sub EVENT_POPUPRESPONSE {
     if ($popupid == 666) {
          #:: Teleport the player to The Plane of Hate
          quest::movepc(186,-393,656,3);
     }
}
```

## pvp

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; mode _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Toggles the PVP setting for the client character that triggered the event.  String can be on, or off.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Turn pvp on
quest::pvp("on");
#:: Turn pvp off
quest::pvp("off");
```

## qs_player_event

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; character_id _(int)_, message _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Adds a record to table `qs_player_events` with the specified parameters.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::qs_player_event($charid,"Triggered an event with this API call in it.")
```

## qs_send_query

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; query _(string)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Send a raw query to the QueryServ process.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
quest::qs_send_query("SELECT * FROM `qs_player_events` WHERE `event_desc` LIKE '%level%' LIMIT 0,1000;");
```

## rain

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; weather _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Changes the rainy weather to the specified setting:  0=none, 1=rain.  See also quest::snow().

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
sub EVENT_ZONE {
     if ($name=~/turmoiltoad/i) {
          #:: Turn on the rain for those left behind
          quest::rain(1);
     }
}
```

## rebind

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; zone_id _(int)_, x _(float)_, y _(float)_, z _(float)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Binds the client character that triggered the event to the specified zone (by Zone ID) at the specified location.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Change bind point to Rivervale, X=0, Y=0, Z=3.13
quest::rebind(19, 0.00, 0.00, 3.13);
```

## removetitle

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; title_set_id _(int)_

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Removes the specified Title Set from the client character that triggered the event.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Example:**

```perl
#:: Remove Title Set 2 (prefix "Arbiter", suffix "Harbinger of the Old World")
quest::removetitle(2);
```

## repopzone

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Parameter(s):**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; None.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **Usage:**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Repops the zone and re-enables spawn timers.

```perl
#:: Repop the zone
quest::repopzone();
```

(Work in Progress)

```perl
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
quest::GetInstanceIDByCharID(const char *zone, int16 version, uint32 char_id)
quest::AssignToInstanceByCharID(uint16 instance_id, uint32 char_id)
quest::RemoveFromInstanceByCharID(uint16 instance_id, uint32 char_id)
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