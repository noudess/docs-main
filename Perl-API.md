> A complete list of Perl scripting resources...

##### **Perl Guides**

*   \[\[Entity Lists - How to Use Them\]\] - By Akkadius
*   \[\[The Power of Entity Variables\]\] - By Akkadius
*   \[\[How To Use Quest Globals\]\] - By Kingly Krab

##### **Saving/Naming Quests**

*   Quests go in the directory **'quests'** (not Quests).
*   Save your quests as a .pl This can be done by going into Notepad --> Save As --> All File Types --> "npcid.pl"
*   If the quest applies to any mob in the zone with the same name (99% of all cases), Quests should be saved in **$EQEmuDir$/quests/zonesn/NPC_NAME.pl (replacing ` with -)**
*   If the quest applies to a specific NPC type in the zone, and there are several npc types with the same name in that zone, quests should be saved in $EQEmuDir$/quests/zonesn/NPCID.pl
*   Server-wide default quest in: $EQEmuDir$/quests/default.pl - Be careful when editing this that you don't delete something that your server uses. Such as the plugin returnitems so npcs dont eat items.
*   For player quests (player.pl) see: \[\[Player Quest Examples\]\]
*   For item quests see: \[\[ItemQuests\]\]
*   For tasks see: \[\[TaskSystemOverview\]\]

##### **Comments**

*   Anything after an # is a comment, and is ignored by the parser. This is useful for leaving notes if you have more than one person working on a quest.
    *   Example of a comment:

sub EVENT_SAY {
	if ($text=~/Hail/i) { #Checks if the text is like Hail, case-insensitive.
		plugin::Whisper("Hail!");
	}
}

##### **Events**

*   A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)

##### **Perl Sub Events** \- These are events defined by the EQEmu Software/Source that trigger inside a Perl script

```perl
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
sub EVENT_ENCOUNTER_LOAD # Triggered when an encounter loads.
sub EVENT_ENCOUNTER_UNLOAD # Triggered when an encounter unloads.
sub EVENT_ENTER # Triggered by any client who enters a mob\'s proximity.
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

#### Text Response Example

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

### Special Text Response Examples

These responses allow you to check for multiple strings within your text variable.

if ($text=~/Hail|Hi|Hello/i) # Will check if the text contains "Hail", "Hi", or "Hello".
if ($text!~/Hail|Hi|Hello/i) # Will check if the text does not contain "Hail", "Hi", or "Hello".

**This uses Perl Regular Expression Matching. See one of the following sites for more info:**

*   [http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlrequick.html](http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlrequick.html)
*   [http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlretut.html](http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlretut.html)
*   [http://www.erudil.com/preqr.pdf](http://www.erudil.com/preqr.pdf)

### **Pre-Exported Variables**

*   A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)
*   Pre-Exported variables are variables that are pre-created by the source typically by certain events or behaviors
*   \[\[Faction Values\]\]

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

### **Function List**

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
<span bitstream="" mono="" sans="" style="color: rgb(0, 130, 0); font-family: Consolas, " vera="">quest::enable_proximity_say() #Required for sub EVENT_PROXIMITY_SAY to work
</span>quest::exp(amount) # Adds 'amount' of exp to user's exp amount. NOTE: This is effected by all experience multipliers. So, a global multiplier of 2.0 will double the amount of experience you specified.
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

### Example
```perl
$client->GetAccountID()
```

```perl
AccountID()
AccountName()
AddAAPoints(number)
AddAlternateCurrencyValue(currency_id, value)
AddCrystals(NumberOfRadiant, NumberOfEbon)
AddEXP(add_exp, conlevel, resexp)
AddLevelBasedExp(exp_percentage, max_level)
AddMoneyToPP(copper, silver, gold, platinum, updateclient)
AddPVPPoints(Points)
AddSkill(skillid, value)
Admin()
AssignTask(taskid, npcid[, enforce_level_requirement]) # use 0 for npcid to assume current npc, 0/1 to enforce level requirement in DB
AssignToInstance(instance_id)
AutoSplitEnabled()
BreakInvis()
CalcPriceMod(other, reverse)
CanHaveSkill(skill_id)
ChangeLastName(in_lastname)
CharacterID()
CheckIncreaseSkill(skillid, chancemodi)
CheckSpecializeIncrease(spell_id)
ClearCompassMark()
ClearZoneFlag(zone_id)
Connected()
DecreaseByID(type, amt)
DeleteItemInInventory(slot_id, quantity, client_update)
Disconnect()
DropItem(slot_id)
Duck()
Escape()
FailTask(taskid)
ForageItem()
Freeze()
GMKill()
GetAAExp()
GetAALevel(skill_id)
GetAAPoints()
GetAccountFlag(flag)
GetAggroCount()
GetAllMoney()
GetAnon()
GetAugmentAt(slot, aug_slot)
GetAugmentIDAt(slot, aug_slot)
GetBaseAGI()
GetBaseCHA()
GetBaseDEX()
GetBaseFace()
GetBaseINT()
GetBaseSTA()
GetBaseSTR()
GetBaseWIS()
GetBecomeNPCLevel()
GetCarriedMoney()
GetCharacterFactionLevel(faction_id)
GetClientVersion()
GetClientVersionBit()
GetCorpseCount()
GetCorpseID(corpse_number)
GetCorpseItemAt(corpse_number, slotid)
GetCustomItemData()
GetDuelTarget()
GetEXP()
GetEbonCrystals()
GetEndurance()
GetEnduranceRatio()
GetFace()
GetFactionLevel(char_id, npc_id, p_race, p_class, p_deity, pFaction, tnpc)
GetFeigned()
GetFreeSpellBookSlot(start_slot)
GetGM()
GetGroup()
GetGroupPoints()
GetHorseId()
GetInstrumentMod(spell_id)
GetIP()
GetInstrumentMod()
GetItemAt(slot)
GetItemIDAt(slot_id)
GetItemInInventory(slot_id)
GetLDoNLosses()
GetLDoNLossesTheme()
GetLDoNPointsTheme(theme)
GetLDoNWins()
GetLDoNWinsTheme()
GetLanguageSkill(n)
GetLastName()
GetMaxEndurance()
GetModCharacterFactionLevel(faction_id) # Returns the character's faction level with race, class, and deity modifiers
GetPVP()
GetPVPPoints()
GetRadiantCrystals()
GetRaid()
GetRaidPoints()
GetRawItemAC()
GetRawSkill(skill_id)
GetSkill(skill_id)
GetSkillPoints()
GetSpellBookSlotBySpellID(spell_id)
GetSpentAA()
GetStartZone() # Returns the zone id number of the character's home city
GetTargetRingX()
GetTargetRingY()
GetTargetRingZ()
GetTaskActivityDoneCount(taskid, activityid)
GetTotalSecondsPlayed()
GetWeight()
GoFish()
GuildID()
GuildRank()
HasSkill(skill_id)
HasZoneFlag(zone_id)
Hungry()
InZone()
IncStats(type, increase_val)
IncreaseLanguageSkill(skill_id, value)
IncreaseSkill(skill_id, value)
IncrementAA(skill_id)
IsBecomeNPC()
IsDueling()
IsGrouped()
IsLD()
IsMedding()
IsRaidGrouped()
IsSitting()
IsTaskActive(taskid)
IsTaskActivityActive(taskid, activityid)
IsTaskCompleted(taskid)
KeyRingAdd()
KeyRingCheck()
Kick()
LearnRecipe()
LeaveGroup()
LoadZoneFlags()
LootToStack(itemid)
MarkCompassLoc(x, y, z)
MaxSkill(skillid)
MemSpell(spell_id, slot, update_client)
MovePC(zoneID, x, y, z, heading)
MovePCInstance(zoneID, instanceID, x, y, z, heading)
NPCSpawn(target_npc, option, respawntime) # Options are: "create", "add", "update", "remove", "delete"
NukeItem(itemnum)
OpenLFGuildWindow()
ReadBook(Book Text, Type)
RefundAA()
RemoveNoRent()
ResetAA()
ResetTaskActivity(taskid, activityid)
ResetTrade()
Save(iCommitNow)
SaveBackup()
ScribeSpell(spell_id, slot, update_client)
SendColoredText(color, msg)
SendMarqueeMessage(type, priority, fade_in, fade_out,  duration, message) # type = color, priority = text opacity, fade_in = 1, fade_out = fade out in MS, duration = duration in MS
SendOPTranslocateConfirm()
SendSound()
SendSpellAnim(targetid, spellid)
SendZoneFlagInfo(to)
SetAAPoints(points)
SetAATitle(txt, save)
SetAccountFlag(flag, value)
SetBaseClass(i)
SetBaseGender(i)
SetBaseRace(i)
SetBecomeNPC(flag)
SetBecomeNPCLevel(level)
SetBindPoint(to_zone, new_x, new_y, new_z)
SetCustomItemData()
SetDeity(i)
SetDuelTarget(set_id)
SetDueling(duel)
SetEXP(set_exp, set_aaxp, resexp)
SetEndurance(Endurance)
SetFactionLevel(char_id, npc_id, char_class, char_race, char_deity)
SetFactionLevel2(char_id, faction_id, char_class, char_race, char_deity, value)
SetFeigned(in_feigned)
SetGM(toggle)
SetHorseId(horseid_in)
SetLanguageSkill(langid, value)
SetMaterial(slot_id, item_id)
SetPVP(toggle)
SetSkill(skill_num, value)
SetSkillPoints(inp)
SetStartZone(zoneid, x, y, z) # Sets the home city bind point. The coordinates x, y, and z are optional.
SetStats(type, increase_val)
SetTint(slot_id, color)
SetTitleSuffix(txt, save)
SetZoneFlag(zone_id)
SignalClient(data)
SlotConvert2(slot)
Stand()
SummonItem(item_id, charges, attune, aug1, aug2, aug3, aug4, aug5)
TGB()
TakeMoneyFromPP(copper, update_client)
TaskTimeLeft(taskid)
Thirsty()
UnFreeze()
Undye()
UnmemSpell(slot, update_client)
UnmemSpellAll(update_client)
UnscribeSpell(slot, update_client)
UnscribeSpellAll(update_client)
UntrainDisc(slot, update_client)
UntrainDiscAll(update_client)
UpdateAdmin(iFromDB)
UpdateGroupAAs()
UpdateLDoNPoints(points, theme)
UpdateTaskActivity(taskID, activityID, count[, hide update client?]) # i.e. $client->UpdateTaskActivity(507, 0, 3) will increment task 507's activity 0 by 3.
UpdateWho(remove)
UseDiscipline(spell_id, target)
WorldKick()
```

# Corpse

```perl
$corpse->AddItem(itemnum, charges, slot)
```

```perl
AddItem(itemnum, charges, slot)
AddLooter(who)
AllowMobLoot(them, slot)
CanMobLoot(charid)
CastRezz(spellid, Caster)
CompleteRezz()
CountItems()
Delete()
GetCharID()
GetCopper()
GetDBID()
GetDecayTime()
GetGold()
GetOwnerName()
GetPlatinum()
GetSilver()
GetWornItem(equipSlot)
IsEmpty()
IsLocked()
IsRezzed()
Lock()
RemoveCash()
RemoveItem(lootslot)
ResetLooter()
SetCash(in_copper, in_silver, in_gold, in_platinum)
SetDecayTimer(decaytime)
Summon(client, spell)
UnLock()
```

# EntityList 

```perl
$entity_list->Object();
```

```perl
CanAddHateForMob(p)
Clear()
ClearClientPetitionQueue()
ClearFeignAggro(targ)
DeleteNPCCorpses()
DeletePlayerCorpses()
DoubleAggro(who)
Fighting(targ)
FindDoor(id)
GetClientByAccID(accid)
GetClientByCharID(iCharID)
GetClientByID(id)
GetClientByName(name)
GetClientByWID(iWID)
GetClientList()
GetCorpseByID(id)
GetCorpseByName(name)
GetCorpseByOwner(client)
GetCorpseList()
GetDoorsByDBID(id)
GetDoorsByID(id)
GetDoorsList()
GetGroupByClient(client)
GetGroupByID(id)
GetGroupByLeaderName(leader)
GetGroupByMob(mob)
GetMob(name)
GetMobByID(id)
GetMobByNpcTypeID(get_id)
GetMobID(id)
GetMobList()
GetNPCByID(id)
GetNPCByNPCTypeID(npc_id)
GetNPCList()
GetObjectByDBID()
GetObjectByID()
GetObjectList()
GetRaidByClient(client)
GetRaidByID(id)
GetRandomClient(x, y, z, range, ClientToExclude)
HalveAggro(who)
MakeNameUnique(name)
MessageClose(sender, skipsender, dist, type, message, ...)
MessageGroup(sender, skipclose, type, message, ...)
MessageStatus(to_guilddbid, to_minstatus, type, message, ...)
OpenDoorsNear(opener)
RemoveAllClients()
RemoveAllCorpses()
RemoveAllDoors()
RemoveAllGroups()
RemoveAllMobs()
RemoveAllNPCs()
RemoveAllObjects()
RemoveAllTraps()
RemoveClient(delete_id)
RemoveCorpse(delete_id)
RemoveDoor(delete_id)
RemoveEntity(id)
RemoveFromHateLists(mob, settoone)
RemoveFromTargets(mob)
RemoveGroup(delete_id)
RemoveMob(delete_id)
RemoveNPC(delete_id)
RemoveNumbers(CLASS, name)
RemoveObject(delete_id)
RemoveTrap(delete_id)
ReplaceWithTarget(pOldMob, pNewTarget)
SignalAllClients(data)
SignalMobsByNPCID(npc_type, signal_id)
```

# Group 

 * $group needs to be fetched from an entity object, for example:  $group = $client->GetGroup())

```perl
CastGroupSpell(caster, spellid)
DisbandGroup()
GetHighestLevel()
GetID()
GetLeader()
GetLeaderName()
GetMember(number) # Returns a client pointer to the group member (NULL if that member doesn't exist)
GetTotalGroupDamage(other)
GroupCount()
GroupMessage(sender, message)
IsGroupMember(client)
IsLeader(leadertest)
SendHPPacketsFrom(newmember)
SendHPPacketsTo(newmember)
SetLeader(newleader)
SplitExp(exp, other)
SplitMoney(copper, silver, gold, platinum)
TeleportGroup(sender, zoneID, x, y, z)
```

# Raid

```perl
$raid->Object();
```

* $raid needs to be fetched from an entity object, for example: $raid = $client->GetRaid())

```perl
BalanceHP()
CastGroupSpell(caster, spellid)
GetClientByIndex(number)
GetGroup()
GetHighestLevel()
GetID()
GetLowestLevel()
GetMember(number)
GetTotalRaidDamage(other)
GroupCount()
IsGroupLeader(client)
IsLeader(client)
IsRaidMember(name) # $raid->IsRaidMember("Hateborne")
RaidCount()
SplitExp(exp, other)
SplitMoney(copper, silver, gold, platinum)
TeleportGroup(sender, zoneID, x, y, z, heading)
TeleportRaid(sender, zoneID, x, y, z, heading)
```

#### **Mob - $mob->Object();**

```perl
AddFeignMemory(attacker)
AddToHateList(other, hate, damage, iYellForHelp, bFrenzy, iBuffTic)
Attack(other, Hand, FromRiposte)
BehindMob(other, playerx, playery)
BuffFadeAll()
BuffFadeByEffect(effectid, skipslot)
BuffFadeBySlot(slot, iRecalcBonuses)
BuffFadeBySpellID(spell_id)
CalculateDistance(x, y, z)
CalculateHeadingToTarget(in_x, in_y)
CalculateNewPosition(x, y, z, speed, checkZ)
CalculateNewPosition2(x, y, z, speed, checkZ)
CameraEffect(duration, intensity, singleclient, serverwide)
CanBuffStack(spellid, caster_level, iFailIfOverwrite)
CanClassEquipItem(item_id)
CanThisClassDodge()
CanThisClassDoubleAttack()
CanThisClassDualWield()
CanThisClassParry()
CanThisClassRiposte()
CastSpell(spell_id, target_id, slot, casttime, mana_cost, resist_adjust)
CastToClient()
CastToCorpse()
CastToMob()
CastToNPC()
CastingSpellID()
ChangeSize(in_size, bNoRestriction)
Charmed()
CheckAggro(other)
CheckAggroAmount(spellid)
CheckHealAggroAmount(spellid)
CheckLoS(other)
CheckLoSToLoc(x, y, z, mob_size)
ClearFeignMemory()
ClearSpecialAbilities()
CombatRange()
Damage(from, damage, spell_id, attack_skill, avoidable, buffslot, iBuffTic)
DelGlobal(varname)
Depop(StartSpawnTimer)
DivineAura()
DoAnim(animnum, type=1)
DoArcheryAttackDmg()
DoKnockback(caster, pushback, pushup)  # $client->DoKnockback($npc, 10, 7) would appear that the NPC knocked the client back
DoMeleeSkillAttackDmg()
DoSpecialAttackDamage(target, skill, max_damage, min_damage, hate_override)
DoThrowingAttackDmg()
DontBuffMeBefore()
DontDotMeBefore()
DontHealMeBefore()
DontRootMeBefore()
DontSnareMeBefore()
Emote(format, ...)
EntityVariableExists()
FaceTarget(MobToFace, update)
FindBuff(spellid)
FindGroundZ(x, y, z_offset)
FindType(type, bOffensive, threshold)
GMMove(x, y, z, heading)
Gate()
GetAA(aa_id)
GetAC()
GetAccuracyRating()
GetAvoidanceRating()
GetAGI()
GetATK()
GetAttackDelay()
GetActSpellCasttime(spell_id, casttime)
GetActSpellCost(spell_id, cost)
GetActSpellDamage(spell_id, value)
GetActSpellDuration(spell_id, duration)
GetActSpellHealing(spell_id, value)
GetActSpellRange(spell_id, range)
GetAggroRange()
GetAllowBeneficial()
GetAppearance()
GetArmorTint(material_slot)
GetAssistRange()
GetBaseGender()
GetBaseRace()
GetBeard()
GetBeardColor()
GetBodyType()
GetBuffSlotFromType(type)
GetCHA()
GetCR()
GetCasterLevel(spell_id)
GetClass()
GetClassLevelFactor()
GetCleanName()
GetCorruption()
GetDEX()
GetDR()
GetDamageAmount(tmob)
GetDeity()
GetDrakkinDetails()
GetDrakkinHeritage()
GetDrakkinTattoo()
GetEntityVariable()
GetEquipment(material_slot)
GetEquipmentColor(material_slot)
GetEquipmentMaterial(material_slot)
GetEyeColor1()
GetEyeColor2()
GetFR()
GetFlurryChance()
GetFollowID()
GetGender()
GetGlobal(varname)
GetHP()
GetHPRatio()
GetHairColor()
GetHairStyle()
GetHaste()
GetHateAmount(tmob, is_dam)
GetHateDamageTop(other)
GetHateList()
GetHateRandom()
GetHateTop()
GetHeading()
GetHelmTexture()
GetID()
GetINT()
GetInvul()
GetItemHPBonuses()
GetItemStat(itemid, stat)
GetLevel()
GetLevelCon(iOtherLevel)
GetLevelHP(tlevel)
GetLuclinFace()
GetMR()
GetMana()
GetManaRatio()
GetMaxAGI()
GetMaxCHA()
GetMaxDEX()
GetMaxHP()
GetMaxINT()
GetMaxMana()
GetMaxSTA()
GetMaxSTR()
GetMaxWIS()
GetModSkillDmgTaken()
GetModVulnerability()
GetMonkHandToHandDamage()
GetMonkHandToHandDelay()
GetNPCTypeID()
GetName()
GetOwnerID()
GetPR()
GetPetID()
GetPetOrder()
GetPetType()
GetRace()
GetResist(type)
GetReverseFactionCon(iOther)
GetRunAnimSpeed()
GetRunspeed()
GetSTA()
GetSTR()
GetShieldTarget()
GetSize()
GetSkill(skill_num)
GetSkillDmgTaken()
GetSpecialAbility(special_ability)
GetSpecialAbilityParam(special_ability, param)
GetSpecializeSkillValue(spell_id)
GetSpellHPBonuses()
GetSpellStat(spell_id, identifier, slot) # Slot is optional.
GetTarget()
GetTexture()
GetWIS()
GetWalkspeed()
GetWaypointH()
GetWaypointID()
GetWaypointPause()
GetWaypointX()
GetWaypointY()
GetWaypointZ()
GetX()
GetY()
GetZ()
GetZoneID()
GoToBind()
HasNPCSpecialAtk()
HasProcs()
HateSummon()
Heal()
HealDamage(amount[, caster])
InterruptSpell(spellid)
IsAIControlled()
IsBeacon()
IsBeneficialAllowed()
IsCasting()
IsClient()
IsCorpse()
IsDoor()
IsEngaged()
IsEnraged()
IsImmuneToSpell(spell_id, caster)
IsInvisible(other)
IsMeleeDisabled()
IsMezzed()
IsMob()
IsMoving()
IsNPC()
IsNPCCorpse()
IsObject()
IsPlayerCorpse()
IsRoamer()
IsRooted()
IsRunning()
IsStunned()
IsTargeted()
IsTrap()
IsWarriorClass()
Kill()
MakePet(spell_id, pettype, name)
MakeTempPet(spell_id, name, duration, target, sticktarg?)
Mesmerize()
Message(type, message)
Message_StringID(type, string_id, distance)
ModSkillDmgTaken()
ModVulnerability()
NPCSpecialAttacks(parse, permtag, reset, remove)
ProcessSpecialAbilities(str)
ProjectileAnim(mob, item_id, IsArrow, speed, angle, tilt, arc)
QuestReward(client, silver, gold, platinum)
RangedAttack()
RemoveFromFeignMemory(attacker)
RemoveNimbusEffect(effectid)
ResistSpell(resist_type, spell_id, caster)
RogueAssassinate(other)
Say(format, language_id)
SendAppearanceEffect(effect1, effect2, effect3, effect4, effect5, specificclient)
SendIllusion(race, gender, texture, helmtexture, face, hairstyle, haircolor, beard, beardcolor, drakkin_heritage, drakkin_tattoo, drakkin_details, size)
SendPosUpdate(iSendToSelf)
SendPosition()
SendTo(new_x, new_y, new_z)
SendToFixZ(new_x, new_y, new_z)
SendWearChange(material_slot)
SetAllowBeneficial()
SetAppearance(app, iIgnoreSelf)
SetBodyType(type, overwrite_orig?)
SetCurrentWP(waypoint)
SetDeltas(delta_x, delta_y, delta_z, delta_h)
SetDisableMelee()
SetEntityVariable(id_num, var)
SetExtraHaste(Haste)
SetFlurryChance()
SetFlyMode(0|1|2|3)
SetFollowID(id)
SetGender(gender)
SetGlobal(varname, newvalue, options, duration, other)
SetHP(hp)
SetHate(other, hate, damage)
SetHeading(iHeading)
SetInvisible(state)
SetInvul(invul)
SetLD(value)
SetLevel(in_level, command)
SetMana(amount)
SetMaxHP()
SetOOCRegen()
SetOwnerID(NewOwnerID)
SetPetID(NewPetID)
SetPetOrder(i)
SetRace(race)
SetRunAnimSpeed(in)
SetRunning()
SetShieldTarget(mob)
SetSlotTint(material_slot, red_tint, green_tint, blue_tint)
SetSpecialAbility(ability, value)
SetSpecialAbilityParam(ability, param, value)
SetTarget(mob)
SetTargetDestSteps(target_steps)
SetTargetable(targetable)
SetTexture(texture)
Shout(format, ...)
SignalClient(client, data)
SpellEffect(effect, duration, finish_delay, zone_wide, unk20, perm_effect, client) # duration, finish_delay, zone_wide, unk20, perm_effect, and client are Optional.
SpellFinished(spell_id, spell_target, mana_cost)
Spin()
StartEnrage()
Stun(duration) # in whole seconds
TarGlobal(varname, value, duration, npcid, charid, zoneid)
TempName(name)
ThrowingAttack()
TypesTempPet(typesid, name, duration, follow, target, sticktarg);
WearChange(material_slot, texture, color)
WipeHateList()
```

# NPC

Example:
```perl
$npc->GetLoottableID();
```

```perl
AI_SetRoambox(iDist, iMaxX, iMinX, iMaxY, iMinY, iDelay)
AddAISpell(priority, spell_id, type, mana_cost, recast_delay, resist_adjust)
AddCash(in_copper, in_silver, in_gold, in_platinum)
AddItem(itemid, charges, equipitem)
AddLootTable()
AddDefensiveProc(spellid, chance)   
AddMeleeProc(spellid, chance)
AddRangedProc(spellid, chance)
AssignWaypoints(grid)
CalculateNewWaypoint()
CheckNPCFactionAlly(other_faction)
ClearItemList()
CountLoot()
DisplayWaypointInfo(to)
DoClassAttacks(target)
GetAccuracyRating()
GetAttackSpeed()
GetCopper()
GetGold()
GetGrid()
GetGuardPointX()
GetGuardPointY()
GetGuardPointZ()
GetLoottableID()
GetMaxDMG()
GetMaxDamage(tlevel)
GetMaxWp()
GetMerchantProbability()
GetMinDMG()
GetNPCFactionID()
GetNPCHate(in_ent)
GetNPCSpellsID()
GetPetSpellID()
GetPlatinum()
GetPrimSkill()
GetPrimaryFaction()
GetSecSkill()
GetSilver()
GetSlowMitigation()
GetSp2()
GetSpawnPointH()
GetSpawnPointID() # Returns spawn2 id
GetSpawnPointX()
GetSpawnPointY()
GetSpawnPointZ()
GetSpellFocusDMG()
GetSpellFocusHeal()
GetSwarmOwner()
GetSwarmTarget()
GetWaypointMax()
IsAnimal()
IsGuarding()
IsOnHatelist(p)
ModifyNPCStat(identifier, newValue)
MoveTo(mtx, mty, mtz, mth, saveguard)
NextGuardPosition()
PauseWandering(pausetime)
PickPocket(thief)
RemoveAISpell(spell_id)
RemoveCash()
RemoveFromHateList(mob)
RemoveItem(item_id, quantity, slot)
RemoveMeleeProc(spell_id)
RemoveDefensiveProc(spell_id)
RemoveDefensiveProc(spell_id)
ResumeWandering()
SaveGuardSpot(iClearGuardSpot)
SetCopper(amt)
SetGold(amt)
SetGrid(grid_)
SetMerchantProbability(amt)
SetNPCFactionID(in)
SetPetSpellID(amt)
SetPlatinum(amt)
SetPrimSkill(skill_type)
SetSaveWaypoint(waypoint)
SetSecSkill(skill_type)
SetSilver(amt)
SetSp2(sg2)
SetSpellFocusDMG()
SetSpellFocusHeal()
SetSwarmTarget()
SetTaunting(tog)
SetWaypointPause()
SignalNPC(signal_id)
StartSwarmTimer(duration)
StopWandering()
UpdateWaypoint(wp_index)
```

#### **Quest Item**

   GetAugment(slot) # Returns an item object for the augment found in the slot supplied
   GetCharges() # Returns the number of charges on an item
   GetID() # Returns the ID of the item
   GetName() # Returns the name of the item
   IsAttuned() # Returns 1 if the item is attuned (instanced no drop)
   IsType(type) # Returns 1 if the item is of the type supplied (valid types are 0=common, 1=container, 2=book)
   ItemSay(text, language) # The item says text, language is optional (currently only goes to item's owner)
   SetScale(multiplier) # Sets the scale multiplier for scaling items.  1.0 = full stats

#### **Object - $object->Object(); (You will have to get $object from an entity list selection or another method)**

   ClearUser()
   Close()
   Delete(reset_state)
   DeleteItem(index)
   Depop()
   EntityVariableExists(id)
   GetDBID()
   GetEntityVariable(id)
   GetHeading()
   GetID()
   GetIcon()
   GetItemID()
   GetModelName()
   GetType()
   GetX()
   GetY()
   GetZ()
   IsGroundSpawn()
   Repop()
   Save()
   SetEntityVariable(id, var)
   SetHeading(heading)
   SetID(set_id)
   SetIcon(icon)
   SetItemID(itemid)
   SetLocation(x, y, z)
   SetModelName(name)
   SetType(type)
   SetX(XPos)
   SetY(YPos)
   SetZ(ZPos)
   StartDecay()
   VarSave()

#### **Door - $object->Object(); (You will have to get $object from an entity list selection or another method)**

   CreateDatabaseEntry()
   GetDoorDBID()
   GetHeading()
   GetID()
   GetIncline()
   GetKeyItem()
   GetLockPick()
   GetModelName()
   GetNoKeyring()
   GetOpenType()
   GetSize()
   GetX()
   GetY()
   GetZ()
   SetHeading(heading)
   SetIncline(type)
   SetKeyItem(type)
   SetLocation(x, y, z)
   SetLockPick(type)
   SetModelName(name)
   SetNoKeyring(type)
   SetOpenType(type)
   SetSize(size)
   SetX(XPos)
   SetY(YPos)
   SetZ(ZPos)

* * *

### Use Reference

##### **$mob->Object(s)**

**$mob->NPCSpecialAttacks(**_parse, permtag, reset, remove_**)**  
**See**: [NPCSpecialAttacks Reference List](http://wiki.eqemulator.org/p?NPC_Special_Attacks)

sub EVENT_SPAWN {
   $npc->NPCSpecialAttacks("Hn", 0);
   #This causes the NPC to never aggro and never help allies.
}

sub EVENT_SAY {
   #This will 'toggle' the flags after checking to see if the npc has them.
   if($text =~/hail/i) {
      $Check = $npc->HasNPCSpecialAtk("Hn");
      if($Check) {
         quest::say("I will now aggro and assist my allies.");
         $npc->NPCSpecialAttacks("Hn", 1);
      } else {
         quest::say("I will no longer aggro and I will stop assisting my allies.");
         $npc->NPCSpecialAttacks("Hn", 0);
      }
   }
}

_**Note**: You can combine all sorts of different NPCSpecialAttacks as the first parameter to obtain the desired result. In this example, "H" and "n" are entirely different._

* * *

#### Additional References

Modifying NPC Stats: \[\[Modify NPC Stat\]\]

Get Item Stats: \[\[Item Stat Identifiers\]\]

Get Spell Stats: \[\[GetSpellStat\]\]