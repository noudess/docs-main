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

* A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)

```
sub EVENT_AGGRO # Triggered when a mob aggros a client.
sub EVENT_AGGRO_SAY # Triggered when a mob is targeted, the player types something, and NPC is in combat.
sub EVENT_ATTACK # Triggered when the NPC is attacked.
sub EVENT_AUGMENT_ITEM # Triggered when a client augments an item.
sub EVENT_AUGMENT_INSERT # Triggered when a client inserts an augment into an item.
sub EVENT_AUGMENT_REMOVE # Triggered when a client removes an augment from an item.
sub EVENT_CAST # Triggered when a client casts a spell.
sub EVENT_CAST_BEGIN # Triggered when a client begins to cast a spell.
sub EVENT_CAST_ON # Triggered when a player casts a spell on a player or NPC.
sub EVENT_CLICKDOOR # Triggered when the client clicks on a door object.
sub EVENT_CLICK_OBJECT # Triggered when the client clicks on an object.
sub EVENT_COMBAT # Triggered when an NPC enters or leaves combat.
sub EVENT_COMBINE_FAILURE # Triggered when a combine is unsuccessful.
sub EVENT_COMBINE_SUCCESS # Triggered when a combine is successful.
sub EVENT_COMMAND # Triggered when a player says anything like a command.
sub EVENT_CONNECT # Triggered when a player connects to the world.
sub EVENT_DEATH # Triggered when the NPC dies. Fires before death finishes.
sub EVENT_DEATH_COMPLETE # Triggered when the NPC dies.
sub EVENT_DESTROY_ITEM # Triggered when a client destroys an item.
sub EVENT_DISCONNECT # Triggered when a player disconnects from the world.
sub EVENT_DISCOVER_ITEM # Triggered when an item is discovered.
sub EVENT_DROP_ITEM # Triggered when a client drops an item.
sub EVENT_DUEL_LOSE # Triggered when a client loses a duel.
sub EVENT_DUEL_WIN # Triggered when a client wins a duel.
sub EVENT_ENTER # Triggered by any client who enters a mob's proximity.
sub EVENT_ENTER_AREA # Triggered when a client enters the area of a mob.
sub EVENT_ENTERZONE # Triggered when a player enters the zone.
sub EVENT_EQUIP_ITEM # Triggered when a player equips an item.
sub EVENT_EXIT # Triggered by any client who leaves a mob's proximity.
sub EVENT_FEIGN_DEATH # Triggered when a client feign death.
sub EVENT_FISH_FAILURE # Triggered when a client fails at fishing.
sub EVENT_FISH_START # Triggered when a client starts fishing.
sub EVENT_FISH_SUCCESS # Triggered when a client succeeds at fishing.
sub EVENT_FORAGE_FAILURE # Triggered when a client fails at foraging.
sub EVENT_FORAGE_SUCCESS # Triggered when a client succeeds at foraging.
sub EVENT_GROUP_CHANGE # Triggered when a group change occurs.
sub EVENT_HATE_LIST # Triggered when a mob's hate list is changed.
sub EVENT_HP # Triggered by a mob's HP dropping below a threshold.
sub EVENT_ITEM # Triggered when an item or money is turned into the mob.
sub EVENT_ITEM_CLICK # Triggered when an item is clicked.
sub EVENT_ITEM_CLICK_CAST # Triggered when a client casts the click effect on an item.
sub EVENT_ITEM_ENTER_ZONE # Called when an item that would trigger EVENT_SCALE_CALC is in the inventory when a player zones in.
sub EVENT_ITEM_TICK # Triggered when the click effect of an item ticks.
sub EVENT_KILLED_MERIT # Triggered on NPC death when a client is in a group credited with doing the most damage to said loot table NPC.
sub EVENT_LEAVE_AREA # Triggered when a client leaves a mob's area.
sub EVENT_LEVEL_UP # Triggered when the player gains a level.
sub EVENT_LOOT # Triggered when player successfully loots an item from a corpse.
sub EVENT_NPC_SLAY # Triggered when an NPC slays another NPC.
sub EVENT_PLAYER_PICKUP # Triggered when a player picks up an object from the ground.
sub EVENT_POPUPRESPONSE # Used with quest::popup.
sub EVENT_PROXIMITY_SAY # Triggered if the client enters a mob's proximity and uses the appropriate text trigger supplied beneath this event. (set quest::enable_proximity_say() and param 7 in q:set_prox)
sub EVENT_RESPAWN # Triggered when a mob respawns.
sub EVENT_SAY # Triggered when a mob is targeted and the player types something.
sub EVENT_SCALE_CALC # Triggered when an item is equipped to scale the item.
sub EVENT_SIGNAL # Triggered by a call to quest::signal() or quest::signalwith().
sub EVENT_SLAY # Triggered whenever an NPC kills someone.
sub EVENT_SPAWN # Triggered when the NPC spawns.
sub EVENT_SPELL_EFFECT_CLIENT # Triggered when the spell lands on a client.
sub EVENT_SPELL_EFFECT_NPC # Triggered when the spell lands on an NPC.
sub EVENT_SPELL_BUFF_TIC_CLIENT # Triggered when the spell ticks on a client.
sub EVENT_SPELL_BUFF_TIC_NPC # Triggered when the spell ticks on an NPC.
sub EVENT_SPELL_EFFECT_TRANSLOCATE_COMPLETE # Triggered when translocation is complete.
sub EVENT_SPELL_FADE # Triggered when a spell fades.
sub EVENT_TARGET_CHANGE # Triggered when a mob changes their current target or clears it.
sub EVENT_TASKACCEPTED # Triggered when a player accepts a task from the task selector window.
sub EVENT_TASK_COMPLETE # Triggered when a player completes a task.
sub EVENT_TASK_FAIL # Triggered when a player fails a task.
sub EVENT_TASK_STAGE_COMPLETE # Triggered when a task stage is completed.
sub EVENT_TASK_UPDATE # Triggered when a player's task is updated.
sub EVENT_TIMER # Triggered by a quest::settimer().
sub EVENT_TRADE # Triggered by beginning a trade.
sub EVENT_UNAUGMENT_ITEM # Triggered when a client removes an augment from an item.
sub EVENT_UNEQUIP_ITEM # Triggered when a client unequips an item.
sub EVENT_WAYPOINT_ARRIVE # Triggered when a mob arrives at a waypoint.
sub EVENT_WAYPOINT_DEPART # Triggered when a mob leaves a waypoint.
sub EVENT_WEAPON_PROC # Triggered when a weapon procs.
sub EVENT_ZONE # Triggered when a player zones.
```

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
quest::addloot(item_id, charges, equipitem) # Adds 'charges' charges of item 'item_id' to the NPC's loot. If 'equipitem' is false or 0, the item will not be used or shown on the NPC.
quest::addldonpoints(points, theme) # Adds 'points' LDoN points for 'theme' LDoN theme.
quest::addskill(skill, value) # Increases 'skill' by 'value' for user.
quest::AssignToInstance(instance_id) # Assigns a single player to an instance.
quest::AssignGroupToInstance(instance_id) # Assigns a group to an instance.
quest::AssignRaidToInstance(instance_id) # Assigns a raid to an instance.
quest::attack(name) # Attacks player 'name'.
quest::attacknpc(entity_id) # Attacks NPC with ID 'entity_id', NOT NPC type ID!
quest::attacknpctype(npc_type_id) # Attacks the first NPC in the zone with npc type 'npc_type_id'.
quest::buryplayercorpse(char_id) # Buries and depops a single corpse of the specified 'char_id'.
quest::castspell(spell_id, target_id) # Casts spell on entity with the entity ID 'target_id' (This is buggy, if it does not work try $npc->CastSpell(spell_id, target_id);).
quest::changedeity(deity_id) # Permanently changes the user's deity to 'deity_id', then kicks to character select.
quest::checktitle(titleset) # Bool value to determine if a player has the specified titleset enabled or not.
quest::ChooseRandom(123, 245, 789...) # Returns one of the items listed in its arguments randomly.
quest::clear_proximity() # Removes a mob's proximity.
quest::clear_zone_flag(zone_id) # Clears a character flag for the zone specified.
quest::collectitems(item_id, remove) # Returns number of item_id that exist in inventory. If remove is true, items are removed as they are counted.
quest::createdoor(modelname, x, y, z, heading, type, size) # Creates a new door.
quest::creategroundobject(itemid, x, y, z, heading, decaytime) # Creates a ground spawn object/item. Leaving decaytime blank will disable decaying.
quest::creategroundobjectfrommodel(model_name, x, y, z, heading, type, decaytime) # Creates a ground spawn object by model. Leaving decaytime blank will disable decaying.
quest::createguild(guild_name, leader_name) # Creates a new guild.
quest::CreateInstance(zone_name, version, expiration_time) # Creates an instance in the given zone using specified version and expiration time. Note: This command will export the Instance ID that it creates!
quest::crosszonesetentityvariablebynpctypeid(npctype_id, id, m_var) # Sets entity variables world wide with specified npctype_id
quest::crosszonesignalclientbycharid(char_id, data) # Signals character id 'char_id' with 'data'.
quest::crosszonesignalclientbyname(name, data) # Signals player 'name' with 'data'.
quest::crosszonesignalnpcbynpctypeid(npctype_id, data) # Signals all NPC entities world wide with specified npctype_id
quest::crosszonemessageplayerbyname(type, name, message) # Messages player 'name' with color 'type' the message 'message'.
quest::delglobal(varname) # Deletes a quest global.
quest::depop(npc_type_id) # A single mob will de-spawn and not start the spawn timer.
quest::depopall(npc_type_id) # Depops every instance of the npc in the zone (quest::depop(npc_type_id)) will only do one NPC at a time.)
quest::depop_withtimer(npc_type_id) # A single mob will de-spawn and start the spawn timer.
quest::depopzone(type) # Depops every NPC in the zone based on 'type', 0 disables the NPCs' spawn timers so they will not repop on their own, 1 allows them to spawn as normal once their timers are up.
quest::DestroyInstance(instance_id) # Destroys the given instance.
quest::ding() # Sends the ding sound to the client.
quest::disable_spawn2(spawn2_id) # Disables this spawn group from spawning another NPC until it is enabled again. Also Depops any current NPCs using this spawn point.
quest::disable_proximity_say() #Disables sub EVENT_PROXIMITY_SAY from triggering.
quest::doanim(anim_num) # Mob will do animation for 'anim_num'.
quest::echo(color, text) # Echoes specified 'text' to console.
quest::emote(text) # Mob will emote 'text'.
quest::enable_spawn2(spawn2_id) # Enables this spawn group to start spawning again once the respawn timer is up for it.
quest::enabletitle(titleset) # Allows player to use titles from the given titleset, assuming they meet all other qualifications (race, class, AAs, item, etc).
quest::enable_proximity_say() #Required for sub EVENT_PROXIMITY_SAY to work
quest::exp(amount) # Adds 'amount' of exp to user's exp amount. NOTE: This is effected by all experience multipliers. So, a global multiplier of 2.0 will double the amount of experience you specified.
quest::faction(faction_id, value, temp) # Give player faction 'value' with 'faction_id'. 'temp' is optional and its values are 0 = Permanent faction with a message, 1 = Temporary faction without a message, 2 = Temporary faction with a message, and 3 = Permanent faction with no message
quest::factionvalue() # Checks factions returning more logical values than $faction (which cannot be changed due to backwards compatiblity, and the values are hardcoded into client.)
quest::FlagInstanceByGroupLeader() # Assigns the group leader's instance to a player
quest::FlagInstanceByRaidLeader() # Assigns the raid leader's instance to a player
quest::FlyMode(0|1|2) # Sets flymode for player where 0 = Off, 1 = On, 2 = Levitate.
quest::follow(entity_id, distance) # Mob starts to follow 'entity_id'. The second field, 'distance', is optional and can be used to set the distance the Mob will follow its target at.
quest::forcedooropen(door_id) # Forces a door with id 'door_id' to open.
quest::forcedoorclose(door_id) # Forces a door with id 'door_id' to close.
quest::getguildnamebyid(guild_id) # Gets a guild name from the 'guild_id' provided.
quest::GetInstanceID(zonename, version) Returns the instanceid of the given zone/verison.
quest::getlevel(type) # Returns average level. 0 = Self, 1 = Group, 2 = Raid, 3 = Raid (if not in Raid then Group, if not in either Self), 4 = Self 2 (max level ever reached).
quest::getplayerburriedcorpsecount(char_id) # Returns how many of the char_id's corpses are marked as being buried.
quest::get_spawn_condition(zone_short, condition_id) # Get the value of a spawn condition
quest::GetSpellResistType(spell_id) # Returns the resist type of 'spell_id'.
quest::GetSpellTargetType(spell_id) # Returns the target type of 'spell_id'.
quest::givecash(copper, silver, gold, platinum) # Gives client coin.
quest::gmmove(x, y, z) # Moves the user that triggered the Event to the provided location.
quest::gmsay(text, color, all_zones?, guild_id, minstatus)
quest::has_zone_flag(zone_id) # Checks for a 'zone_id' zone flag.
quest::incstat(statid, 0-126) # Increases a stat by value x2 (Str=0, Sta=1, Agi=2, Dex=3, Int=4, Wis=5, Cha=6)
quest::InsertQuestGlobal(charid, npcid, zoneid, varname, value, duration) # Creates a Quest Global.
quest::IsBeneficialSpell(spell_id) # Returns true if 'spell_id' is beneficial.
quest::IsEffectInSpell(spell_id, effect_id) # Returns true if spell effect 'effect_id' is in 'spell_id'.
quest::isdooropen(door_id) # Checks if 'door_id' is currently open.
quest::isdisctome(item_id) # Checks if 'item_id' is a discipline tome.
quest::IsRunning() # Checks if an NPC is walking (returns 0) or running (returns 1)
quest::itemlink(item_id) # Mob sends a tell to you with a link to an item. (not to be confused with quest::varlink which can be used in a message this must have its own line)
quest::level(newlevel) # Sets the user's level to 'newlevel'.
quest::me(text) # Does a name-less emote.
quest::MerchantCountItem(merchant_npc_id, item_id) # returns the number of that item in stock.
quest::MerchantSetItem(merchant_npc_id, item_id, quantity) # Changes the number of the item that the merchant has available to sell.
quest::modifynpcstat(identifier, value) # Changes NPC stats on the fly. Changes are not saved to DB.
quest::movegrp(zone_id, x, y, z) # Moves the user's Group that triggered the Event to the provided zone and location.
quest::movepc(zone_id, x, y, z, heading) # Moves the user that triggered the Event to the provided zone and location. Heading is optional.
quest::MovePCInstance(zone_id, instance_id, x, y, z) # Moves a player to instance 'instance_id' of the zone 'zone_id' at 'x', 'y', and 'z'.
quest::moveto(x, y, z, heading, saveguardspot) # NPC moves to the set coordinates with 'heading' and 'saveguardspot' being optional. NPC will path back unless 'saveguardspot' is set to 1.
quest::npcfeature(feature, setting) # Temporarily changes the NPC's appearance.
quest::npcgender(gender) # Temporarily changes the NPC's gender.
quest::npcrace(raceid) # Temporarily changes the NPC's race.
quest::npcsize(size) # Temporarily changes the NPC's size.
quest::npctexture(texture) # Temporarily changes the NPC's texture.
quest::pathto(x, y, z) # Causes the npc to use path finding to walk to 'x', 'y', and 'z'.
quest::pause(time) # Forces the NPC to take a break for a certain time.
quest::permaclass(class_id) # Permanently changes the user's class to 'class_id'.
quest::permagender(gender_id) # Permanently changes the user's gender to 'gender_id'. 0 = Male, 1 = Female, 2 = Neuter.
quest::permarace(race_id) # Permanently changes the user's race to 'race_id', then kicks to character select.
quest::playerfeature(feature, setting) # Temporarily changes the player's appearance.
quest::playergender(gender) # Temporarily changes the player's gender.
quest::playerrace(raceid) # Temporarily changes the player's race.
quest::playersize(size) # Temporaririly changes the player's size.
quest::playertexture(texture) # Temporarily changes the player's texture.
quest::popup(title, text, popup_id, buttons, duration) # Creates a popup window with the given text. 'popup_id', 'buttons', and 'duration' are optional. The popup will vanish after 'duration' seconds (never if 'duration' is 0). For 'buttons' 0 = Just an OK button, 1 = Yes and No Buttons. This is used in conjunction with sub EVENT_POPUPRESPONSE.
quest::pvp(on|off) # Sets PVP on|off for user.
quest::rain(1|0) or quest::snow(1|0) # Makes it rain or snow in zone.
quest::rebind(zone_id, x, y, z) # Binds the user that triggered the Event to the provided zone and location.
quest::removetitle(titleset) # Removes the specified titleset from a player.
quest::repopzone() # Repops the zone, in the same way the command #repop does. It will also re-enable spawn timers if disabled.
quest::respawn(npc_type, grid) # Respawn specified NPC type on grid.
quest::resume() # Resumes a stopped pathing grid.
quest::safemove() # Moves user to zone's safe x, y, and z coordinates.
quest::save() # Saves player data.
quest::say(text, language_id) # Mob will say 'text'. 'language_id' is optional, and determines what language the NPC will speak in.
quest::saylink(phrase, silent?, linkname) # This is for creating a say link.
quest::scribespells(maxlevel, minlevel) # Scribes all spells up to the specified level.
quest::selfcast(spell_id) # Forces the client to cast 'spell_id' spell on themselves.
quest::setallskill(value) # Sets all skills to 'value'.
quest::setanim(npc_type_id, animnum) # Adds appearance changes to 'npc_type_id' for animation 'animnum'.
quest::sethp(hp_percent) # Sets the HP of an NPC to 'hp_percent'.
quest::setglobal(varname, value, options, duration) # Sets a quest global named 'varname' to value 'value' for 'options' for 'duration'.
quest::setguild(guild_id, rank) # Adds player to 'guild_id' with a 'rank'.
quest::setlanguage(skill_id, 0-100) # Sets a language to value.
quest::setnexthpevent(hp_percent) # Set a HP threshold for EVENT_HP. If the mob's HP falls below this threshold hp_percent, an event will be generated with the percent in $hpevent.
quest::setnextinchpevent(hp_percent) # Set a HP threshold for EVENT_HP. If the mob's HP gets healed past this threshold hp_percent, an event will be generated with the percent in $inchpevent.
quest::SetRunning(value) # Set to 0 for walk, 1 for running.
quest::setskill(skill_id, value) # Sets a single skill to a value.
quest::setsky(0-255) # Changes the sky.
quest::setstat(stat_id, 0-252) # Sets a stat to value (Str=0, Sta=1, Agi=2, Dex=3, Int=4; Wis=5, Cha=6)
quest::settarget(type, id) # Quest mob targets 'id' by 'type' (npctype or entity).
quest::settime(hour, minute, [update world]) # Sets zone time of day. Sky/lighting changes acordingly. Update world is invisible and defaults to true. Use of a "0" results in a disjointed zoned that functions on it's own time system for events.
quest::settimer(timer_name, seconds) # Starts timer 'timer_name' for use with EVENT_TIMER. You can have multiple timers that trigger every 'seconds'.
quest::settimerMS(timer_name, milliseconds) # Same as quest::settimer() except time is in milliseconds.
quest::shout(text) # Mob will shout 'text'.
quest::shout2(text) # Mob will shout 'text' across all zones.
quest::spawn_condition(zone_short_name, condition_id, value) # Uses variables in the spawn_conditions table for spawning or despawning chosen NPCs in a given zone.
quest::spawn_from_spawn2(spawn2_id) # Allows multiple spawns to be spawned from a single spawn group even while the existing NPC for that spawn group is up.
quest::set_proximity(minx, maxx, miny, maxy, minz, maxz, bsay) # Creates a proximity, if a client moves into or out of the bounds specified, proper events are generated. A mob may only have one proximity. 'minz' and 'maxz' are optional. Set bsay = 1 to enable proximity say checks.
quest::set_zone_flag(zone_id) # Flags a character for 'zone_id' zone.
quest::sfollow() # Turns off follow.
quest::showgrid(grid) # Displays an in-game path based on a waypoint 'grid'.
quest::showpath(x, y, z) # Displays an in-game path based on path finding using coordinates 'x', 'y', and 'z'.
quest::signal(npc_id, wait) # cause an EVENT_SIGNAL on all mobs in the zone with this NPC type, with $signalid = 0. wait is an optional time to wait in ms before sending signal.
quest::signalwith(npc_id, signal_id, wait) # same as signal(), except it sets $signal to the supplied signal_id. wait is an optional time to wait in ms before sending signal.
quest::spawn(npc_type_id, grid, guildwarset, x, y, z) # Spawn 'npc_type_id' on 'grid' with 'guildwarset' (use 0) at 'x', 'y', and 'z'.
quest::spawn2(npc_type_id, grid, guildwarset, x, y, z, heading) # Spawn 'npc_type_id' on 'grid' with 'guildwarset' (use 0) at 'x', 'y', and 'z' facing 'heading'.
quest::start(grid_id) # Assigns the grid to an NPC and starts the grid 'grid_id' on the NPC.
quest::stop() # Stops a moving NPC.
quest::stopalltimers() # Stops all current timers on the mob (NPC or client).
quest::stoptimer(timer_name) # Stops the timer 'timer_name'.
quest::summonburriedplayercorpse(char_id, x, y, z, heading) # Summons a single buried corpse of the specified 'char_id' to the specified location.
quest::summonallplayercorpses(char_id, x, y, z, heading) # Summons all corpses belonging to the specified 'char_id' to the specified location.
quest::summonitem(item_id, charges) # Summons 'item_id' to user that triggered Event. Charges is the number of charges, or number of items in the stack depending on the item type, it is also optional.
quest::surname(surname) # Changes user's surname to 'surname'.
quest::targlobal(varname, value, duration, npc_id, char_id, zone_id) # Sets a quest global.
quest::toggle_spawn_event(event_id, enable, reset_base) # Toggle a spawn event.
quest::traindisc(tome_id) # Trains the discipline that corresponds to the item 'tome_id'. See quest::isdisctome() to test if an item is a discipline tome.
quest::traindiscs(maxlevel, minlevel) # Trains all disciplines up to the specified level. To train up to any level, use $ulevel as the variable.
quest::updatespawntimer(spawn2id, milliseconds) # Sets the time left until the next respawn in the database.
quest::unique_spawn(npc_type, grid, guildwarset, x, y, z, heading) # Just like quest::spawn() except it will not spawn it if one of that 'npc_type' is already in the zone.
quest::unscribespells() # Unscribes all your spells.
quest::untraindiscs() # Untrains all learned disciplines.
quest::varlink(item_id) # This is for creating an item link to be used in a variable.
quest::voicetell(clientname, type, race, gender) # Plays the specified audio macro on the player's client.
quest::we(color_id, text) # Server-wide emote.
quest::wearchange(slot, texture) # Allows setting visible slots to any valid texture/model for that slot.
quest::write(file, string) # Writes 'string' to a file named 'file'.
quest::ze(color_id, text) # Zone-wide emote.
quest::Zone(zone) # Sends the user to the specified zone (short name).
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
$corpse->AddItem(itemnum, charges, slot)
$corpse->AddLooter(who)
$corpse->AllowMobLoot(them, slot)
$corpse->CanMobLoot(charid)
$corpse->CastRezz(spellid, Caster)
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
$corpse->GetWornItem(equipSlot)
$corpse->IsEmpty()
$corpse->IsLocked()
$corpse->IsRezzed()
$corpse->Lock()
$corpse->RemoveCash()
$corpse->RemoveItem(lootslot)
$corpse->ResetLooter()
$corpse->SetCash(in_copper, in_silver, in_gold, in_platinum)
$corpse->SetDecayTimer(decaytime)
$corpse->Summon(client, spell)
$corpse->UnLock()
```

# EntityList 

```perl
$entity_list->CanAddHateForMob(p)
$entity_list->Clear()
$entity_list->ClearClientPetitionQueue()
$entity_list->ClearFeignAggro(targ)
$entity_list->DeleteNPCCorpses()
$entity_list->DeletePlayerCorpses()
$entity_list->DoubleAggro(who)
$entity_list->Fighting(targ)
$entity_list->FindDoor(id)
$entity_list->GetClientByAccID(accid)
$entity_list->GetClientByCharID(iCharID)
$entity_list->GetClientByID(id)
$entity_list->GetClientByName(name)
$entity_list->GetClientByWID(iWID)
$entity_list->GetClientList()
$entity_list->GetCorpseByID(id)
$entity_list->GetCorpseByName(name)
$entity_list->GetCorpseByOwner(client)
$entity_list->GetCorpseList()
$entity_list->GetDoorsByDBID(id)
$entity_list->GetDoorsByID(id)
$entity_list->GetDoorsList()
$entity_list->GetGroupByClient(client)
$entity_list->GetGroupByID(id)
$entity_list->GetGroupByLeaderName(leader)
$entity_list->GetGroupByMob(mob)
$entity_list->GetMob(name)
$entity_list->GetMobByID(id)
$entity_list->GetMobByNpcTypeID(get_id)
$entity_list->GetMobID(id)
$entity_list->GetMobList()
$entity_list->GetNPCByID(id)
$entity_list->GetNPCByNPCTypeID(npc_id)
$entity_list->GetNPCList()
$entity_list->GetObjectByDBID()
$entity_list->GetObjectByID()
$entity_list->GetObjectList()
$entity_list->GetRaidByClient(client)
$entity_list->GetRaidByID(id)
$entity_list->GetRandomClient(x, y, z, range, ClientToExclude)
$entity_list->HalveAggro(who)
$entity_list->MakeNameUnique(name)
$entity_list->MessageClose(sender, skipsender, dist, type, message, ...)
$entity_list->MessageGroup(sender, skipclose, type, message, ...)
$entity_list->MessageStatus(to_guilddbid, to_minstatus, type, message, ...)
$entity_list->OpenDoorsNear(opener)
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
$entity_list->RemoveEntity(id)
$entity_list->RemoveFromHateLists(mob, settoone)
$entity_list->RemoveFromTargets(mob)
$entity_list->RemoveGroup(delete_id)
$entity_list->RemoveMob(delete_id)
$entity_list->RemoveNPC(delete_id)
$entity_list->RemoveNumbers(CLASS, name)
$entity_list->RemoveObject(delete_id)
$entity_list->RemoveTrap(delete_id)
$entity_list->ReplaceWithTarget(pOldMob, pNewTarget)
$entity_list->SignalAllClients(data)
$entity_list->SignalMobsByNPCID(npc_type, signal_id)
```

# Group 

 * $group needs to be fetched from an entity object, for example:  $group = $client->GetGroup())

```perl
$group->CastGroupSpell(caster, spellid)
$group->DisbandGroup()
$group->GetHighestLevel()
$group->GetID()
$group->GetLeader()
$group->GetLeaderName()
$group->GetMember(number) # Returns a client pointer to the group member (NULL if that member doesn't exist)
$group->GetTotalGroupDamage(other)
$group->GroupCount()
$group->GroupMessage(sender, message)
$group->IsGroupMember(client)
$group->IsLeader(leadertest)
$group->SendHPPacketsFrom(newmember)
$group->SendHPPacketsTo(newmember)
$group->SetLeader(newleader)
$group->SplitExp(exp, other)
$group->SplitMoney(copper, silver, gold, platinum)
$group->TeleportGroup(sender, zoneID, x, y, z)
```

# Raid

```perl
$raid->Object();
```

* $raid needs to be fetched from an entity object, for example: $raid = $client->GetRaid())

```perl
$raid->BalanceHP()
$raid->CastGroupSpell(caster, spellid)
$raid->GetClientByIndex(number)
$raid->GetGroup()
$raid->GetHighestLevel()
$raid->GetID()
$raid->GetLowestLevel()
$raid->GetMember(number)
$raid->GetTotalRaidDamage(other)
$raid->GroupCount()
$raid->IsGroupLeader(client)
$raid->IsLeader(client)
$raid->IsRaidMember(name) # $raid->IsRaidMember("Hateborne")
$raid->RaidCount()
$raid->SplitExp(exp, other)
$raid->SplitMoney(copper, silver, gold, platinum)
$raid->TeleportGroup(sender, zoneID, x, y, z, heading)
TeleportRaid(sender, zoneID, x, y, z, heading)
```

# Mob

* Important Note! Most of the $mob objects also work when used with $client

```perl
$mob->AddFeignMemory(attacker)
$mob->AddToHateList(other, hate, damage, iYellForHelp, bFrenzy, iBuffTic)
$mob->Attack(other, Hand, FromRiposte)
$mob->BehindMob(other, playerx, playery)
$mob->BuffFadeAll()
$mob->BuffFadeByEffect(effectid, skipslot)
$mob->BuffFadeBySlot(slot, iRecalcBonuses)
$mob->BuffFadeBySpellID(spell_id)
$mob->CalculateDistance(x, y, z)
$mob->CalculateHeadingToTarget(in_x, in_y)
$mob->CalculateNewPosition(x, y, z, speed, checkZ)
$mob->CalculateNewPosition2(x, y, z, speed, checkZ)
$mob->CameraEffect(duration, intensity, singleclient, serverwide)
$mob->CanBuffStack(spellid, caster_level, iFailIfOverwrite)
$mob->CanClassEquipItem(item_id)
$mob->CanThisClassDodge()
$mob->CanThisClassDoubleAttack()
$mob->CanThisClassDualWield()
$mob->CanThisClassParry()
$mob->CanThisClassRiposte()
$mob->CastSpell(spell_id, target_id, slot, casttime, mana_cost, resist_adjust)
$mob->CastToClient()
$mob->CastToCorpse()
$mob->CastToMob()
$mob->CastToNPC()
$mob->CastingSpellID()
$mob->ChangeSize(in_size, bNoRestriction)
$mob->Charmed()
$mob->CheckAggro(other)
$mob->CheckAggroAmount(spellid)
$mob->CheckHealAggroAmount(spellid)
$mob->CheckLoS(other)
$mob->CheckLoSToLoc(x, y, z, mob_size)
$mob->ClearFeignMemory()
$mob->ClearSpecialAbilities()
$mob->CombatRange()
$mob->Damage(from, damage, spell_id, attack_skill, avoidable, buffslot, iBuffTic)
$mob->DelGlobal(varname)
$mob->Depop(StartSpawnTimer)
$mob->DivineAura()
$mob->DoAnim(animnum, type=1)
$mob->DoArcheryAttackDmg()
$mob->DoKnockback(caster, pushback, pushup)  # $client->DoKnockback($npc, 10, 7) would appear that the NPC knocked the client back
$mob->DoMeleeSkillAttackDmg()
$mob->DoSpecialAttackDamage(target, skill, max_damage, min_damage, hate_override)
$mob->DoThrowingAttackDmg()
$mob->DontBuffMeBefore()
$mob->DontDotMeBefore()
$mob->DontHealMeBefore()
$mob->DontRootMeBefore()
$mob->DontSnareMeBefore()
$mob->Emote(format, ...)
$mob->EntityVariableExists()
$mob->FaceTarget(MobToFace, update)
$mob->FindBuff(spellid)
$mob->FindGroundZ(x, y, z_offset)
$mob->FindType(type, bOffensive, threshold)
$mob->GMMove(x, y, z, heading)
$mob->Gate()
$mob->GetAA(aa_id)
$mob->GetAC()
$mob->GetAccuracyRating()
$mob->GetAvoidanceRating()
$mob->GetAGI()
$mob->GetATK()
$mob->GetAttackDelay()
$mob->GetActSpellCasttime(spell_id, casttime)
$mob->GetActSpellCost(spell_id, cost)
$mob->GetActSpellDamage(spell_id, value)
$mob->GetActSpellDuration(spell_id, duration)
$mob->GetActSpellHealing(spell_id, value)
$mob->GetActSpellRange(spell_id, range)
$mob->GetAggroRange()
$mob->GetAllowBeneficial()
$mob->GetAppearance()
$mob->GetArmorTint(material_slot)
$mob->GetAssistRange()
$mob->GetBaseGender()
$mob->GetBaseRace()
$mob->GetBeard()
$mob->GetBeardColor()
$mob->GetBodyType()
$mob->GetBuffSlotFromType(type)
$mob->GetCHA()
$mob->GetCR()
$mob->GetCasterLevel(spell_id)
$mob->GetClass()
$mob->GetClassLevelFactor()
$mob->GetCleanName()
$mob->GetCorruption()
$mob->GetDEX()
$mob->GetDR()
$mob->GetDamageAmount(tmob)
$mob->GetDeity()
$mob->GetDrakkinDetails()
$mob->GetDrakkinHeritage()
$mob->GetDrakkinTattoo()
$mob->GetEntityVariable()
$mob->GetEquipment(material_slot)
$mob->GetEquipmentColor(material_slot)
$mob->GetEquipmentMaterial(material_slot)
$mob->GetEyeColor1()
$mob->GetEyeColor2()
$mob->GetFR()
$mob->GetFlurryChance()
$mob->GetFollowID()
$mob->GetGender()
$mob->GetGlobal(varname)
$mob->GetHP()
$mob->GetHPRatio()
$mob->GetHairColor()
$mob->GetHairStyle()
$mob->GetHaste()
$mob->GetHateAmount(tmob, is_dam)
$mob->GetHateDamageTop(other)
$mob->GetHateList()
$mob->GetHateRandom()
$mob->GetHateTop()
$mob->GetHeading()
$mob->GetHelmTexture()
$mob->GetID()
$mob->GetINT()
$mob->GetInvul()
$mob->GetItemHPBonuses()
$mob->GetItemStat(itemid, stat)
$mob->GetLevel()
$mob->GetLevelCon(iOtherLevel)
$mob->GetLevelHP(tlevel)
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
$mob->GetModSkillDmgTaken()
$mob->GetModVulnerability()
$mob->GetMonkHandToHandDamage()
$mob->GetMonkHandToHandDelay()
$mob->GetNPCTypeID()
$mob->GetName()
$mob->GetOwnerID()
$mob->GetPR()
$mob->GetPetID()
$mob->GetPetOrder()
$mob->GetPetType()
$mob->GetRace()
$mob->GetResist(type)
$mob->GetReverseFactionCon(iOther)
$mob->GetRunAnimSpeed()
$mob->GetRunspeed()
$mob->GetSTA()
$mob->GetSTR()
$mob->GetShieldTarget()
$mob->GetSize()
$mob->GetSkill(skill_num)
$mob->GetSkillDmgTaken()
$mob->GetSpecialAbility(special_ability)
$mob->GetSpecialAbilityParam(special_ability, param)
$mob->GetSpecializeSkillValue(spell_id)
$mob->GetSpellHPBonuses()
$mob->GetSpellStat(spell_id, identifier, slot) # Slot is optional.
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
$mob->HasNPCSpecialAtk()
$mob->HasProcs()
$mob->HateSummon()
$mob->Heal()
$mob->HealDamage(amount[, caster])
$mob->InterruptSpell(spellid)
$mob->IsAIControlled()
$mob->IsBeacon()
$mob->IsBeneficialAllowed()
$mob->IsCasting()
$mob->IsClient()
$mob->IsCorpse()
$mob->IsDoor()
$mob->IsEngaged()
$mob->IsEnraged()
$mob->IsImmuneToSpell(spell_id, caster)
$mob->IsInvisible(other)
$mob->IsMeleeDisabled()
$mob->IsMezzed()
$mob->IsMob()
$mob->IsMoving()
$mob->IsNPC()
$mob->IsNPCCorpse()
$mob->IsObject()
$mob->IsPlayerCorpse()
$mob->IsRoamer()
$mob->IsRooted()
$mob->IsRunning()
$mob->IsStunned()
$mob->IsTargeted()
$mob->IsTrap()
$mob->IsWarriorClass()
$mob->Kill()
$mob->MakePet(spell_id, pettype, name)
$mob->MakeTempPet(spell_id, name, duration, target, sticktarg?)
$mob->Mesmerize()
$mob->Message(type, message)
$mob->Message_StringID(type, string_id, distance)
$mob->ModSkillDmgTaken()
$mob->ModVulnerability()
$mob->NPCSpecialAttacks(parse, permtag, reset, remove)
$mob->ProcessSpecialAbilities(str)
$mob->ProjectileAnim(mob, item_id, IsArrow, speed, angle, tilt, arc)
$mob->QuestReward(client, silver, gold, platinum)
$mob->RangedAttack()
$mob->RemoveFromFeignMemory(attacker)
$mob->RemoveNimbusEffect(effectid)
$mob->ResistSpell(resist_type, spell_id, caster)
$mob->RogueAssassinate(other)
$mob->Say(format, language_id)
$mob->SendAppearanceEffect(effect1, effect2, effect3, effect4, effect5, specificclient)
$mob->SendIllusion(race, gender, texture, helmtexture, face, hairstyle, haircolor, beard, beardcolor, drakkin_heritage, drakkin_tattoo, $mob->drakkin_details, size)
$mob->SendPosUpdate(iSendToSelf)
$mob->SendPosition()
$mob->SendTo(new_x, new_y, new_z)
$mob->SendToFixZ(new_x, new_y, new_z)
$mob->SendWearChange(material_slot)
$mob->SetAllowBeneficial()
$mob->SetAppearance(app, iIgnoreSelf)
$mob->SetBodyType(type, overwrite_orig?)
$mob->SetCurrentWP(waypoint)
$mob->SetDeltas(delta_x, delta_y, delta_z, delta_h)
$mob->SetDisableMelee()
$mob->SetEntityVariable(id_num, var)
$mob->SetExtraHaste(Haste)
$mob->SetFlurryChance()
$mob->SetFlyMode(0|1|2|3)
$mob->SetFollowID(id)
$mob->SetGender(gender)
$mob->SetGlobal(varname, newvalue, options, duration, other)
$mob->SetHP(hp)
$mob->SetHate(other, hate, damage)
$mob->SetHeading(iHeading)
$mob->SetInvisible(state)
$mob->SetInvul(invul)
$mob->SetLD(value)
$mob->SetLevel(in_level, command)
$mob->SetMana(amount)
$mob->SetMaxHP()
$mob->SetOOCRegen()
$mob->SetOwnerID(NewOwnerID)
$mob->SetPetID(NewPetID)
$mob->SetPetOrder(i)
$mob->SetRace(race)
$mob->SetRunAnimSpeed(in)
$mob->SetRunning()
$mob->SetShieldTarget(mob)
$mob->SetSlotTint(material_slot, red_tint, green_tint, blue_tint)
$mob->SetSpecialAbility(ability, value)
$mob->SetSpecialAbilityParam(ability, param, value)
$mob->SetTarget(mob)
$mob->SetTargetDestSteps(target_steps)
$mob->SetTargetable(targetable)
$mob->SetTexture(texture)
$mob->Shout(format, ...)
$mob->SignalClient(client, data)
$mob->SpellEffect(effect, duration, finish_delay, zone_wide, unk20, perm_effect, client) # duration, finish_delay, zone_wide, unk20, $mob->perm_effect, and client are Optional.
$mob->SpellFinished(spell_id, spell_target, mana_cost)
$mob->Spin()
$mob->StartEnrage()
$mob->Stun(duration) # in whole seconds
$mob->TarGlobal(varname, value, duration, npcid, charid, zoneid)
$mob->TempName(name)
$mob->ThrowingAttack()
$mob->TypesTempPet(typesid, name, duration, follow, target, sticktarg);
$mob->WearChange(material_slot, texture, color)
$mob->WipeHateList()
```

# NPC

```perl
$npc->AI_SetRoambox(iDist, iMaxX, iMinX, iMaxY, iMinY, iDelay)
$npc->AddAISpell(priority, spell_id, type, mana_cost, recast_delay, resist_adjust)
$npc->AddCash(in_copper, in_silver, in_gold, in_platinum)
$npc->AddItem(itemid, charges, equipitem)
$npc->AddLootTable()
$npc->AddDefensiveProc(spellid, chance)   
$npc->AddMeleeProc(spellid, chance)
$npc->AddRangedProc(spellid, chance)
$npc->AssignWaypoints(grid)
$npc->CalculateNewWaypoint()
$npc->CheckNPCFactionAlly(other_faction)
$npc->ClearItemList()
$npc->CountLoot()
$npc->DisplayWaypointInfo(to)
$npc->DoClassAttacks(target)
$npc->GetAccuracyRating()
$npc->GetAttackSpeed()
$npc->GetCopper()
$npc->GetGold()
$npc->GetGrid()
$npc->GetGuardPointX()
$npc->GetGuardPointY()
$npc->GetGuardPointZ()
$npc->GetLoottableID()
$npc->GetMaxDMG()
$npc->GetMaxDamage(tlevel)
$npc->GetMaxWp()
$npc->GetMerchantProbability()
$npc->GetMinDMG()
$npc->GetNPCFactionID()
$npc->GetNPCHate(in_ent)
$npc->GetNPCSpellsID()
$npc->GetPetSpellID()
$npc->GetPlatinum()
$npc->GetPrimSkill()
$npc->GetPrimaryFaction()
$npc->GetSecSkill()
$npc->GetSilver()
$npc->GetSlowMitigation()
$npc->GetSp2()
$npc->GetSpawnPointH()
$npc->GetSpawnPointID() # Returns spawn2 id
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
$npc->IsOnHatelist(p)
$npc->ModifyNPCStat(identifier, newValue)
$npc->MoveTo(mtx, mty, mtz, mth, saveguard)
$npc->NextGuardPosition()
$npc->PauseWandering(pausetime)
$npc->PickPocket(thief)
$npc->RemoveAISpell(spell_id)
$npc->RemoveCash()
$npc->RemoveFromHateList(mob)
$npc->RemoveItem(item_id, quantity, slot)
$npc->RemoveMeleeProc(spell_id)
$npc->RemoveDefensiveProc(spell_id)
$npc->RemoveDefensiveProc(spell_id)
$npc->ResumeWandering()
$npc->SaveGuardSpot(iClearGuardSpot)
$npc->SetCopper(amt)
$npc->SetGold(amt)
$npc->SetGrid(grid_)
$npc->SetMerchantProbability(amt)
$npc->SetNPCFactionID(in)
$npc->SetPetSpellID(amt)
$npc->SetPlatinum(amt)
$npc->SetPrimSkill(skill_type)
$npc->SetSaveWaypoint(waypoint)
$npc->SetSecSkill(skill_type)
$npc->SetSilver(amt)
$npc->SetSp2(sg2)
$npc->SetSpellFocusDMG()
$npc->SetSpellFocusHeal()
$npc->SetSwarmTarget()
$npc->SetTaunting(tog)
$npc->SetWaypointPause()
$npc->SignalNPC(signal_id)
$npc->StartSwarmTimer(duration)
$npc->StopWandering()
$npc->UpdateWaypoint(wp_index)
```

# Quest Items

* Below objects require you to fetch an item instance via an item getter, for example:

```perl
$item = $client->GetItemAt(slot);
$item->GetCharges();
```

```perl
GetAugment(slot) # Returns an item object for the augment found in the slot supplied
GetCharges() # Returns the number of charges on an item
GetID() # Returns the ID of the item
GetName() # Returns the name of the item
IsAttuned() # Returns 1 if the item is attuned (instanced no drop)
IsType(type) # Returns 1 if the item is of the type supplied (valid types are 0=common, 1=container, 2=book)
ItemSay(text, language) # The item says text, language is optional (currently only goes to item's owner)
SetScale(multiplier) # Sets the scale multiplier for scaling items.  1.0 = full stats
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
$object->Delete(reset_state)
$object->DeleteItem(index)
$object->Depop()
$object->EntityVariableExists(id)
$object->GetDBID()
$object->GetEntityVariable(id)
$object->GetHeading()
$object->GetID()
$object->GetIcon()
$object->GetItemID()
$object->GetModelName()
$object->GetType()
$object->GetX()
$object->GetY()
$object->GetZ()
$object->IsGroundSpawn()
$object->Repop()
$object->Save()
$object->SetEntityVariable(id, var)
$object->SetHeading(heading)
$object->SetID(set_id)
$object->SetIcon(icon)
$object->SetItemID(itemid)
$object->SetLocation(x, y, z)
$object->SetModelName(name)
$object->SetType(type)
$object->SetX(XPos)
$object->SetY(YPos)
$object->SetZ(ZPos)
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
$door->CreateDatabaseEntry()
$door->GetDoorDBID()
$door->GetHeading()
$door->GetID()
$door->GetIncline()
$door->GetKeyItem()
$door->GetLockPick()
$door->GetModelName()
$door->GetNoKeyring()
$door->GetOpenType()
$door->GetSize()
$door->GetX()
$door->GetY()
$door->GetZ()
$door->SetHeading(heading)
$door->SetIncline(type)
$door->SetKeyItem(type)
$door->SetLocation(x, y, z)
$door->SetLockPick(type)
$door->SetModelName(name)
$door->SetNoKeyring(type)
$door->SetOpenType(type)
$door->SetSize(size)
$door->SetX(XPos)
$door->SetY(YPos)
$door->SetZ(ZPos)
```

# Perl Debugging

* Run the perl file against the perl processor for syntax errors. (e.g. perl <filename.pl>)
* Reload the quest in game. #reloadquest or #rq
* See any recent API errors. #questerrors
* Peek at the zone console and see if any hints appear there. Also look at the zone logfile.