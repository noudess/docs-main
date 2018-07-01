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

$(document).on("click", ".example-link", function() { var example = $("#example-"+$(this).data("example")); if(example.is(":visible")) { example.slideUp("fast"); } else { example.slideDown("slow"); }});

sub EVENT_AGGRO # Triggered when a mob aggros a client.
sub EVENT\_AGGRO\_SAY # Triggered when a mob is targeted, the player types something, and NPC is in combat.
sub EVENT_ATTACK # Triggered when the NPC is attacked.
sub EVENT\_AUGMENT\_ITEM # Triggered when a client augments an item.
sub EVENT\_AUGMENT\_INSERT # Triggered when a client inserts an augment into an item.
sub EVENT\_AUGMENT\_REMOVE # Triggered when a client removes an augment from an item.
sub EVENT_CAST # Triggered when a client casts a spell.
sub EVENT\_CAST\_BEGIN # Triggered when a client begins to cast a spell.
sub EVENT\_CAST\_ON # Triggered when a player casts a spell on a player or NPC.
sub EVENT_CLICKDOOR # Triggered when the client clicks on a door object.
sub EVENT\_CLICK\_OBJECT # Triggered when the client clicks on an object.
sub EVENT_COMBAT # Triggered when an NPC enters or leaves combat.
sub EVENT\_COMBINE\_FAILURE # Triggered when a combine is unsuccessful.
sub EVENT\_COMBINE\_SUCCESS # Triggered when a combine is successful.
sub EVENT_COMMAND # Triggered when a player says anything like a command.
sub EVENT_CONNECT # Triggered when a player connects to the world.
sub EVENT_DEATH # Triggered when the NPC dies. Fires before death finishes.
sub EVENT\_DEATH\_COMPLETE # Triggered when the NPC dies.
sub EVENT\_DESTROY\_ITEM # Triggered when a client destroys an item.
sub EVENT_DISCONNECT # Triggered when a player disconnects from the world.
sub EVENT\_DISCOVER\_ITEM # Triggered when an item is discovered.
sub EVENT\_DROP\_ITEM # Triggered when a client drops an item.
sub EVENT\_DUEL\_LOSE # Triggered when a client loses a duel.
sub EVENT\_DUEL\_WIN # Triggered when a client wins a duel.
sub EVENT\_ENCOUNTER\_LOAD # Triggered when an encounter loads.
sub EVENT\_ENCOUNTER\_UNLOAD # Triggered when an encounter unloads.
sub EVENT_ENTER # Triggered by any client who enters a mob's proximity.
sub EVENT\_ENTER\_AREA # Triggered when a client enters the area of a mob.
sub EVENT_ENTERZONE # Triggered when a player enters the zone.
sub EVENT\_EQUIP\_ITEM # Triggered when a player equips an item.
sub EVENT_EXIT # Triggered by any client who leaves a mob's proximity.
sub EVENT\_FEIGN\_DEATH # Triggered when a client feign death.
sub EVENT\_FISH\_FAILURE # Triggered when a client fails at fishing.
sub EVENT\_FISH\_START # Triggered when a client starts fishing.
sub EVENT\_FISH\_SUCCESS # Triggered when a client succeeds at fishing.
sub EVENT\_FORAGE\_FAILURE # Triggered when a client fails at foraging.
sub EVENT\_FORAGE\_SUCCESS # Triggered when a client succeeds at foraging.
sub EVENT\_GROUP\_CHANGE # Triggered when a group change occurs.
sub EVENT\_HATE\_LIST # Triggered when a mob's hate list is changed.
sub EVENT_HP # Triggered by a mob's HP dropping below a threshold.
sub EVENT_ITEM # Triggered when an item or money is turned into the mob.
sub EVENT\_ITEM\_CLICK # Triggered when an item is clicked.
sub EVENT\_ITEM\_CLICK_CAST # Triggered when a client casts the click effect on an item.
sub EVENT\_ITEM\_ENTER\_ZONE # Called when an item that would trigger EVENT\_SCALE_CALC is in the inventory when a player zones in.
sub EVENT\_ITEM\_TICK # Triggered when the click effect of an item ticks.
sub EVENT\_KILLED\_MERIT # Triggered on NPC death when a client is in a group credited with doing the most damage to said loot table NPC.
sub EVENT\_LEAVE\_AREA # Triggered when a client leaves a mob's area.
sub EVENT\_LEVEL\_UP # Triggered when the player gains a level.
sub EVENT_LOOT # Triggered when player successfully loots an item from a corpse.
sub EVENT\_NPC\_SLAY # Triggered when an NPC slays another NPC.
sub EVENT\_PLAYER\_PICKUP # Triggered when a player picks up an object from the ground.
sub EVENT_POPUPRESPONSE # Used with quest::popup.
sub EVENT\_PROXIMITY\_SAY # Triggered if the client enters a mob's proximity and uses the appropriate text trigger supplied beneath this event. (set quest::enable\_proximity\_say() and param 7 in q:set_prox)
sub EVENT_RESPAWN # Triggered when a mob respawns.
sub EVENT_SAY # Triggered when a mob is targeted and the player types something.
sub EVENT\_SCALE\_CALC # Triggered when an item is equipped to scale the item.
sub EVENT_SIGNAL # Triggered by a call to quest::signal() or quest::signalwith().
sub EVENT_SLAY # Triggered whenever an NPC kills someone.
sub EVENT_SPAWN # Triggered when the NPC spawns.
sub EVENT\_SPELL\_EFFECT_CLIENT # Triggered when the spell lands on a client.
sub EVENT\_SPELL\_EFFECT_NPC # Triggered when the spell lands on an NPC.
sub EVENT\_SPELL\_BUFF\_TIC\_CLIENT # Triggered when the spell ticks on a client.
sub EVENT\_SPELL\_BUFF\_TIC\_NPC # Triggered when the spell ticks on an NPC.
sub EVENT\_SPELL\_EFFECT\_TRANSLOCATE\_COMPLETE # Triggered when translocation is complete.
sub EVENT\_SPELL\_FADE # Triggered when a spell fades.
sub EVENT\_TARGET\_CHANGE # Triggered when a mob changes their current target or clears it.
sub EVENT_TASKACCEPTED # Triggered when a player accepts a task from the task selector window.
sub EVENT\_TASK\_COMPLETE # Triggered when a player completes a task.
sub EVENT\_TASK\_FAIL # Triggered when a player fails a task.
sub EVENT\_TASK\_STAGE_COMPLETE # Triggered when a task stage is completed.
sub EVENT\_TASK\_UPDATE # Triggered when a player's task is updated.
sub EVENT_TIMER # Triggered by a quest::settimer().
sub EVENT_TRADE # Triggered by beginning a trade.
sub EVENT\_UNAUGMENT\_ITEM # Triggered when a client removes an augment from an item.
sub EVENT\_UNEQUIP\_ITEM # Triggered when a client unequips an item.
sub EVENT\_WAYPOINT\_ARRIVE # Triggered when a mob arrives at a waypoint.
sub EVENT\_WAYPOINT\_DEPART # Triggered when a mob leaves a waypoint.
sub EVENT\_WEAPON\_PROC # Triggered when a weapon procs.
sub EVENT_ZONE # Triggered when a player zones.

#### **Text Response Example**s

All speaking responses are included in a **$text** variable (This variable is defined by the EQEmu Software)

if ($text=~/hail/i) # Note the /i. This means it is case-insensitive. It is always better to include this.
if ($text=~/Hello/) # Would match "Hello", but not "hello".
if ($text=~/hello/) # Would match "hello", but not "Hello".
if ($text=~/hello/i) # Would match "Hello" and "hello".
if ($text=~/me/) # Would match the "me" in "name", but not the "me" in "NAME".
if ($text=~/\\bme\\b/) # Would not match the "me" in "name" or the "me" in "NAME". The "\\b" means there must not be text next to the match so "me" must be by itself.
if ($text=~/^me$/i) # Would only match if "me" is the only text said. The "^" tells what must be the first thing said and the "$" tells what must be the last thing.

**Special Text Response Examples**

These responses allow you to check for multiple strings within your text variable.

if ($text=~/Hail|Hi|Hello/i) # Will check if the text contains "Hail", "Hi", or "Hello".
if ($text!~/Hail|Hi|Hello/i) # Will check if the text does not contain "Hail", "Hi", or "Hello".

**This uses Perl Regular Expression Matching. See one of the following sites for more info:**

*   [http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlrequick.html](http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlrequick.html)
*   [http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlretut.html](http://aspn.activestate.com/ASPN/docs/ActivePerl/lib/Pod/perlretut.html)
*   [http://www.erudil.com/preqr.pdf](http://www.erudil.com/preqr.pdf)

##### **Pre-Exported Variables**

*   A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)
*   Pre-Exported variables are variables that are pre-created by the source typically by certain events or behaviors
*   \[\[Faction Values\]\]

$activity\_id # Returns the ID of the task stage completed (in EVENT\_TASK\_STAGE\_COMPLETE); Returns the ID of the task updated or complete (in EVENT\_TASK\_COMPLETE, EVENT\_TASK\_UPDATE)
$charid # Returns the character ID of the client that triggered the Event or a negative value if no client was involved.
$class # Returns the class of the user that triggered the event.
$caster\_id # Returns the ID of the caster (in EVENT\_SPELL\_EFFECT\_CLIENT, EVENT\_SPELL\_EFFECT\_NPC, EVENT\_SPELL\_BUFF\_TIC\_CLIENT, EVENT\_SPELL\_BUFF\_TIC_NPC)
$combat\_state # Returns 1 for starting combat, returns 0 for leaving combat (in EVENT\_COMBAT)
$corpse # Returns the ID of the corpse in which an item was looted (in EVENT_LOOT)
$donecount # Return the number of hand-ins completed \[i.e. 5 of 10 Crushbone Belts, the 5 would be returned\] (in EVENT\_TASK\_COMPLETE, EVENT\_TASK\_UPDATE)
$doorid # Returns ID of the door clicked (in EVENT\_CLICK\_DOOR)
$faction # Returns the faction level number of the user with the NPC
$fished\_items # Returns the item ID of fished item (in EVENT\_FISH_SUCCESS)
$foraged\_item # Returns the item ID of foraged item (in EVENT\_FORAGE_SUCCESS)
$grouped # Returns 0 or 1 depending on group status (in EVENT\_GROUP\_CHANGED)
$hate\_state # Return the state of hate (in EVENT\_HATE_LIST)
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
$itemid # Return the item ID of items used (in EVENT\_ITEM\_CLICK\_CAST, EVENT\_ITEM_CLICK)
$itemname # Returns the item name of items used (in EVENT\_ITEM\_CLICK\_CAST, EVENT\_ITEM_CLICK)
$killed # Returns the NPC id of the npc slain (in EVENT\_NPC\_SLAY)
$killer\_damage # Returns the damage of the mob's killer's killing blow (in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE)
$killer\_id # Returns the entity ID of a mob's killer (in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE)
$killer\_skill # Returns the skill ID of the mob's killer's killing blow (in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE)
$killer\_spell # Returns the spell ID of the mob's killer's spell (in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE)
$hasitem{itemid} # Checks the character's inventory master slots for an item
$hpevent # Used to identify the HP Event set via quest::setnexthpevent() (in EVENT_HP)
$hpratio # Returns HP Ratio
$inchpevent # Used potentially for the incoming hp event or next hp event (in EVENT_HP)
$instanceid # Returns the instance ID of the current zone
$instanceversion # Returns the instance version
$langid # Returns the language id the player/npc is currently using. (in EVENT\_SAY, EVENT\_AGGRO\_SAY, EVENT\_PROXIMITY_SAY)
$looted\_charges # Returns the charges of the looted item (in EVENT\_LOOT)
$looted\_id # Returns the ID of the looted item (in EVENT\_LOOT)
$oncursor{itemid} # Checks the character's front item on the cursor for an item
$objectid # Returns the object id of the clicked item (in EVENT\_CLICK\_OBJECT)
$mlevel # Returns the level of the mob that the user triggered the Event on.
$mname # Returns the mob's name (returns non-clean, for a clean name use $npc->GetCleanName();).
$mobid # Returns the npc_types ID of the mob that the user triggered the Event on.
$name # Returns the name of the user that triggered the Event.
$picked\_up\_id # Returns the item id picked up (in EVENT\_PLAYER\_PICKUP)
$popupid # Returns the ID of the popup window (in EVENT_POPUPRESPONSE)
$race # Returns the race of the user that triggered the Event.
$raided # Returns 0 or 1 depending on group status (in EVENT\_GROUP\_CHANGED)
$recipe # Returns the ID of the recipe (in EVENT\_COMBINE\_SUCCESS, EVENT\_COMBINE\_FAILURE)
$signal # Returns the value of a signal sent using quest::signalwith() (in EVENT_SIGNAL)
$slotid # Returns the slot ID of the item used (in EVENT\_ITEM\_CLICK\_CAST, EVENT\_ITEM_CLICK)
$spell\_id # Returns the ID of the spell cast (in EVENT\_CAST, EVENT\_CAST\_ON, EVENT\_CAST\_BEGIN)
$status # Returns the account status of the user that triggered the Event.
$target\_zone\_id # Returns the ID of the zone to enter, such as in casting ports (in EVENT_ZONE)
$targetid # Returns the entity id of the NPC's current (or last) target.
$targetname # Returns the name of the NPC's current (or last) target.
$task\_id # Returns the task ID of the task accepted (in EVENT\_TASKACCEPTED), stage completed (in EVENT\_TASK\_STAGE\_COMPLETE), task failed (in EVENT\_TASK\_FAIL), task updated or completed (in EVENT\_TASK\_COMPLETE, EVENT\_TASK_UPDATE)
$text # The text sent by players to an NPC (in EVENT\_SAY), from an NPC (in EVENT\_AGGRO\_SAY), spoken by player when nearby the NPC (in EVENT\_PROXIMITY_SAY)
$timer # Returns the value used when creating a timer with quest::settimer() (in EVENT_TIMER)
$uguild_id # Returns the ID of the guild of the user that triggered the Event.
$uguildrank # Returns the guild rank of the user that triggered the Event.
$ulevel # Returns the level of the user that triggered the Event.
$userid # Returns the ID of the user that triggered the Event.
$version # Returns the version of the door clicked (in EVENT_CLICKDOOR)
$wp # Returns current waypoint (in EVENT\_WAYPOINT\_ARRIVE and EVENT\_WAYPOINT\_DEPART)
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

##### **Function List**

*   A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/questmgr.cpp](https://github.com/EQEmu/Server/blob/master/zone/questmgr.cpp)

quest::addloot(item\_id, charges, equipitem) # Adds 'charges' charges of item 'item\_id' to the NPC's loot. If 'equipitem' is false or 0, the item will not be used or shown on the NPC.
quest::addldonpoints(points, theme) # Adds 'points' LDoN points for 'theme' LDoN theme.
quest::addskill(skill, value) # Increases 'skill' by 'value' for user.
quest::AssignToInstance(instance_id) # Assigns a single player to an instance.
quest::AssignGroupToInstance(instance_id) # Assigns a group to an instance.
quest::AssignRaidToInstance(instance_id) # Assigns a raid to an instance.
quest::attack(name) # Attacks player 'name'.
quest::attacknpc(entity\_id) # Attacks NPC with ID 'entity\_id', NOT NPC type ID!
quest::attacknpctype(npc\_type\_id) # Attacks the first NPC in the zone with npc type 'npc\_type\_id'.
quest::buryplayercorpse(char\_id) # Buries and depops a single corpse of the specified 'char\_id'.
quest::castspell(spell\_id, target\_id) # Casts spell on entity with the entity ID 'target\_id' (This is buggy, if it does not work try $npc->CastSpell(spell\_id, target_id);).
quest::changedeity(deity\_id) # Permanently changes the user's deity to 'deity\_id', then kicks to character select.
quest::checktitle(titleset) # Bool value to determine if a player has the specified titleset enabled or not.
quest::ChooseRandom(123, 245, 789...) # Returns one of the items listed in its arguments randomly.
quest::clear_proximity() # Removes a mob's proximity.
quest::clear\_zone\_flag(zone_id) # Clears a character flag for the zone specified.
quest::collectitems(item\_id, remove) # Returns number of item\_id that exist in inventory. If remove is true, items are removed as they are counted.
quest::createdoor(modelname, x, y, z, heading, type, size) # Creates a new door.
quest::creategroundobject(itemid, x, y, z, heading, decaytime) # Creates a ground spawn object/item. Leaving decaytime blank will disable decaying.
quest::creategroundobjectfrommodel(model_name, x, y, z, heading, type, decaytime) # Creates a ground spawn object by model. Leaving decaytime blank will disable decaying.
quest::createguild(guild\_name, leader\_name) # Creates a new guild.
quest::CreateInstance(zone\_name, version, expiration\_time) # Creates an instance in the given zone using specified version and expiration time. Note: This command will export the Instance ID that it creates!
quest::crosszonesetentityvariablebynpctypeid(npctype\_id, id, m\_var) # Sets entity variables world wide with specified npctype_id
quest::crosszonesignalclientbycharid(char\_id, data) # Signals character id 'char\_id' with 'data'.
quest::crosszonesignalclientbyname(name, data) # Signals player 'name' with 'data'.
quest::crosszonesignalnpcbynpctypeid(npctype\_id, data) # Signals all NPC entities world wide with specified npctype\_id
quest::crosszonemessageplayerbyname(type, name, message) # Messages player 'name' with color 'type' the message 'message'.
quest::delglobal(varname) # Deletes a quest global.
quest::depop(npc\_type\_id) # A single mob will de-spawn and not start the spawn timer.
quest::depopall(npc\_type\_id) # Depops every instance of the npc in the zone (quest::depop(npc\_type\_id)) will only do one NPC at a time.)
quest::depop\_withtimer(npc\_type_id) # A single mob will de-spawn and start the spawn timer.
quest::depopzone(type) # Depops every NPC in the zone based on 'type', 0 disables the NPCs' spawn timers so they will not repop on their own, 1 allows them to spawn as normal once their timers are up.
quest::DestroyInstance(instance_id) # Destroys the given instance.
quest::ding() # Sends the ding sound to the client.
quest::disable\_spawn2(spawn2\_id) # Disables this spawn group from spawning another NPC until it is enabled again. Also Depops any current NPCs using this spawn point.
quest::disable\_proximity\_say() #Disables sub EVENT\_PROXIMITY\_SAY from triggering.
quest::doanim(anim\_num) # Mob will do animation for 'anim\_num'.
quest::echo(color, text) # Echoes specified 'text' to console.
quest::emote(text) # Mob will emote 'text'.
quest::enable\_spawn2(spawn2\_id) # Enables this spawn group to start spawning again once the respawn timer is up for it.
quest::enabletitle(titleset) # Allows player to use titles from the given titleset, assuming they meet all other qualifications (race, class, AAs, item, etc).
quest::enable\_proximity\_say() #Required for sub EVENT\_PROXIMITY\_SAY to work quest::exp(amount) # Adds 'amount' of exp to user's exp amount. NOTE: This is effected by all experience multipliers. So, a global multiplier of 2.0 will double the amount of experience you specified.
quest::faction(faction\_id, value, temp) # Give player faction 'value' with 'faction\_id'. 'temp' is optional and its values are 0 = Permanent faction with a message, 1 = Temporary faction without a message, 2 = Temporary faction with a message, and 3 = Permanent faction with no message
quest::factionvalue() # Checks factions returning more logical values than $faction (which cannot be changed due to backwards compatiblity, and the values are hardcoded into client.)
quest::FlagInstanceByGroupLeader() # Assigns the group leader's instance to a player
quest::FlagInstanceByRaidLeader() # Assigns the raid leader's instance to a player
quest::FlyMode(0|1|2) # Sets flymode for player where 0 = Off, 1 = On, 2 = Levitate.
quest::follow(entity\_id, distance) # Mob starts to follow 'entity\_id'. The second field, 'distance', is optional and can be used to set the distance the Mob will follow its target at.
quest::forcedooropen(door\_id) # Forces a door with id 'door\_id' to open.
quest::forcedoorclose(door\_id) # Forces a door with id 'door\_id' to close.
quest::getguildnamebyid(guild\_id) # Gets a guild name from the 'guild\_id' provided.
quest::GetInstanceID(zonename, version) Returns the instanceid of the given zone/verison.
quest::getlevel(type) # Returns average level. 0 = Self, 1 = Group, 2 = Raid, 3 = Raid (if not in Raid then Group, if not in either Self), 4 = Self 2 (max level ever reached).
quest::getplayerburriedcorpsecount(char\_id) # Returns how many of the char\_id's corpses are marked as being buried.
quest::get\_spawn\_condition(zone\_short, condition\_id) # Get the value of a spawn condition
quest::GetSpellResistType(spell\_id) # Returns the resist type of 'spell\_id'.
quest::GetSpellTargetType(spell\_id) # Returns the target type of 'spell\_id'.
quest::givecash(copper, silver, gold, platinum) # Gives client coin.
quest::gmmove(x, y, z) # Moves the user that triggered the Event to the provided location.
quest::gmsay(text, color, all\_zones?, guild\_id, minstatus) 
quest::has\_zone\_flag(zone\_id) # Checks for a 'zone\_id' zone flag.
quest::incstat(statid, 0-126) # Increases a stat by value x2 (Str=0, Sta=1, Agi=2, Dex=3, Int=4, Wis=5, Cha=6)
quest::InsertQuestGlobal(charid, npcid, zoneid, varname, value, duration) # Creates a Quest Global.
quest::IsBeneficialSpell(spell\_id) # Returns true if 'spell\_id' is beneficial.
quest::IsEffectInSpell(spell\_id, effect\_id) # Returns true if spell effect 'effect\_id' is in 'spell\_id'.
quest::isdooropen(door\_id) # Checks if 'door\_id' is currently open.
quest::isdisctome(item\_id) # Checks if 'item\_id' is a discipline tome.
quest::IsRunning() # Checks if an NPC is walking (returns 0) or running (returns 1)
quest::itemlink(item_id) # Mob sends a tell to you with a link to an item. (not to be confused with quest::varlink which can be used in a message this must have its own line)
quest::level(newlevel) # Sets the user's level to 'newlevel'.
quest::me(text) # Does a name-less emote.
quest::MerchantCountItem(merchant\_npc\_id, item_id) # returns the number of that item in stock.
quest::MerchantSetItem(merchant\_npc\_id, item_id, quantity) # Changes the number of the item that the merchant has available to sell.
quest::modifynpcstat(identifier, value) # Changes NPC stats on the fly. Changes are not saved to DB.
quest::movegrp(zone_id, x, y, z) # Moves the user's Group that triggered the Event to the provided zone and location.
quest::movepc(zone_id, x, y, z, heading) # Moves the user that triggered the Event to the provided zone and location. Heading is optional.
quest::MovePCInstance(zone\_id, instance\_id, x, y, z) # Moves a player to instance 'instance\_id' of the zone 'zone\_id' at 'x', 'y', and 'z'.
quest::moveto(x, y, z, heading, saveguardspot) # NPC moves to the set coordinates with 'heading' and 'saveguardspot' being optional. NPC will path back unless 'saveguardspot' is set to 1.
quest::npcfeature(feature, setting) # Temporarily changes the NPC's appearance.
quest::npcgender(gender) # Temporarily changes the NPC's gender.
quest::npcrace(raceid) # Temporarily changes the NPC's race.
quest::npcsize(size) # Temporarily changes the NPC's size.
quest::npctexture(texture) # Temporarily changes the NPC's texture.
quest::pathto(x, y, z) # Causes the npc to use path finding to walk to 'x', 'y', and 'z'.
quest::pause(time) # Forces the NPC to take a break for a certain time.
quest::permaclass(class\_id) # Permanently changes the user's class to 'class\_id'.
quest::permagender(gender\_id) # Permanently changes the user's gender to 'gender\_id'. 0 = Male, 1 = Female, 2 = Neuter.
quest::permarace(race\_id) # Permanently changes the user's race to 'race\_id', then kicks to character select.
quest::playerfeature(feature, setting) # Temporarily changes the player's appearance.
quest::playergender(gender) # Temporarily changes the player's gender.
quest::playerrace(raceid) # Temporarily changes the player's race.
quest::playersize(size) # Temporaririly changes the player's size.
quest::playertexture(texture) # Temporarily changes the player's texture.
quest::popup(title, text, popup\_id, buttons, duration) # Creates a popup window with the given text. 'popup\_id', 'buttons', and 'duration' are optional. The popup will vanish after 'duration' seconds (never if 'duration' is 0). For 'buttons' 0 = Just an OK button, 1 = Yes and No Buttons. This is used in conjunction with sub EVENT_POPUPRESPONSE.
quest::pvp(on|off) # Sets PVP on|off for user.
quest::rain(1|0) or quest::snow(1|0) # Makes it rain or snow in zone.
quest::rebind(zone_id, x, y, z) # Binds the user that triggered the Event to the provided zone and location.
quest::removetitle(titleset) # Removes the specified titleset from a player.
quest::repopzone() # Repops the zone, in the same way the command #repop does. It will also re-enable spawn timers if disabled.
quest::respawn(npc_type, grid) # Respawn specified NPC type on grid.
quest::resume() # Resumes a stopped pathing grid.
quest::safemove() # Moves user to zone's safe x, y, and z coordinates.
quest::save() # Saves player data.
quest::say(text, language\_id) # Mob will say 'text'. 'language\_id' is optional, and determines what language the NPC will speak in.
quest::saylink(phrase, silent?, linkname) # This is for creating a say link.
quest::scribespells(maxlevel, minlevel) # Scribes all spells up to the specified level.
quest::selfcast(spell\_id) # Forces the client to cast 'spell\_id' spell on themselves.
quest::setallskill(value) # Sets all skills to 'value'.
quest::setanim(npc\_type\_id, animnum) # Adds appearance changes to 'npc\_type\_id' for animation 'animnum'.
quest::sethp(hp\_percent) # Sets the HP of an NPC to 'hp\_percent'.
quest::setglobal(varname, value, options, duration) # Sets a quest global named 'varname' to value 'value' for 'options' for 'duration'.
quest::setguild(guild\_id, rank) # Adds player to 'guild\_id' with a 'rank'.
quest::setlanguage(skill_id, 0-100) # Sets a language to value.
quest::setnexthpevent(hp\_percent) # Set a HP threshold for EVENT\_HP. If the mob's HP falls below this threshold hp_percent, an event will be generated with the percent in $hpevent.
quest::setnextinchpevent(hp\_percent) # Set a HP threshold for EVENT\_HP. If the mob's HP gets healed past this threshold hp_percent, an event will be generated with the percent in $inchpevent.
quest::SetRunning(value) # Set to 0 for walk, 1 for running. 
quest::setskill(skill_id, value) # Sets a single skill to a value.
quest::setsky(0-255) # Changes the sky.
quest::setstat(stat_id, 0-252) # Sets a stat to value (Str=0, Sta=1, Agi=2, Dex=3, Int=4; Wis=5, Cha=6)
quest::settarget(type, id) # Quest mob targets 'id' by 'type' (npctype or entity).
quest::settime(hour, minute, \[update world\]) # Sets zone time of day. Sky/lighting changes acordingly. Update world is invisible and defaults to true. Use of a "0" results in a disjointed zoned that functions on it's own time system for events. 
quest::settimer(timer\_name, seconds) # Starts timer 'timer\_name' for use with EVENT_TIMER. You can have multiple timers that trigger every 'seconds'. 
quest::settimerMS(timer_name, milliseconds) # Same as quest::settimer() except time is in milliseconds.
quest::shout(text) # Mob will shout 'text'.
quest::shout2(text) # Mob will shout 'text' across all zones.
quest::spawn\_condition(zone\_short\_name, condition\_id, value) # Uses variables in the spawn_conditions table for spawning or despawning chosen NPCs in a given zone.
quest::spawn\_from\_spawn2(spawn2_id) # Allows multiple spawns to be spawned from a single spawn group even while the existing NPC for that spawn group is up.
quest::set_proximity(minx, maxx, miny, maxy, minz, maxz, bsay) # Creates a proximity, if a client moves into or out of the bounds specified, proper events are generated. A mob may only have one proximity. 'minz' and 'maxz' are optional. Set bsay = 1 to enable proximity say checks.
quest::set\_zone\_flag(zone\_id) # Flags a character for 'zone\_id' zone.
quest::sfollow() # Turns off follow.
quest::showgrid(grid) # Displays an in-game path based on a waypoint 'grid'.
quest::showpath(x, y, z) # Displays an in-game path based on path finding using coordinates 'x', 'y', and 'z'.
quest::signal(npc\_id, wait) # cause an EVENT\_SIGNAL on all mobs in the zone with this NPC type, with $signalid = 0. wait is an optional time to wait in ms before sending signal.
quest::signalwith(npc\_id, signal\_id, wait) # same as signal(), except it sets $signal to the supplied signal_id. wait is an optional time to wait in ms before sending signal.
quest::spawn(npc\_type\_id, grid, guildwarset, x, y, z) # Spawn 'npc\_type\_id' on 'grid' with 'guildwarset' (use 0) at 'x', 'y', and 'z'.
quest::spawn2(npc\_type\_id, grid, guildwarset, x, y, z, heading) # Spawn 'npc\_type\_id' on 'grid' with 'guildwarset' (use 0) at 'x', 'y', and 'z' facing 'heading'.
quest::start(grid\_id) # Assigns the grid to an NPC and starts the grid 'grid\_id' on the NPC.
quest::stop() # Stops a moving NPC.
quest::stopalltimers() # Stops all current timers on the mob (NPC or client).
quest::stoptimer(timer\_name) # Stops the timer 'timer\_name'.
quest::summonburriedplayercorpse(char\_id, x, y, z, heading) # Summons a single buried corpse of the specified 'char\_id' to the specified location.
quest::summonallplayercorpses(char\_id, x, y, z, heading) # Summons all corpses belonging to the specified 'char\_id' to the specified location.
quest::summonitem(item\_id, charges) # Summons 'item\_id' to user that triggered Event. Charges is the number of charges, or number of items in the stack depending on the item type, it is also optional.
quest::surname(surname) # Changes user's surname to 'surname'.
quest::targlobal(varname, value, duration, npc\_id, char\_id, zone_id) # Sets a quest global.
quest::toggle\_spawn\_event(event\_id, enable, reset\_base) # Toggle a spawn event.
quest::traindisc(tome\_id) # Trains the discipline that corresponds to the item 'tome\_id'. See quest::isdisctome() to test if an item is a discipline tome.
quest::traindiscs(maxlevel, minlevel) # Trains all disciplines up to the specified level. To train up to any level, use $ulevel as the variable.
quest::updatespawntimer(spawn2id, milliseconds) # Sets the time left until the next respawn in the database.
quest::unique\_spawn(npc\_type, grid, guildwarset, x, y, z, heading) # Just like quest::spawn() except it will not spawn it if one of that 'npc_type' is already in the zone.
quest::unscribespells() # Unscribes all your spells.
quest::untraindiscs() # Untrains all learned disciplines.
quest::varlink(item_id) # This is for creating an item link to be used in a variable.
quest::voicetell(clientname, type, race, gender) # Plays the specified audio macro on the player's client.
quest::we(color_id, text) # Server-wide emote.
quest::wearchange(slot, texture) # Allows setting visible slots to any valid texture/model for that slot.
quest::write(file, string) # Writes 'string' to a file named 'file'.
quest::ze(color_id, text) # Zone-wide emote.
quest::Zone(zone) # Sends the user to the specified zone (short name).

##### **Conditionals**

**Syntax:**

if($variable1 \[operator\] $variable2) {
	quest::commands;
}

**Example:**

if($variable1 \[operator\] $variable2) {
	quest::commands;
}
elsif($variable1 \[someotheroperator\] $variable2) {
	quest::commands;
}
else {
	quest::commands;
}

Note, special operators apply to string comparisons in Perl!

**Operators:**

$1 == $2 # If variable $1 is the same as variable $2, carry on.
$1 != $2 # If variable $1 is NOT the same as variable $2, carry on.
$1 > $2 # If variable $1 is greater than variable $2, carry on.
$1 < $2 # If variable $1 is less than variable $2, carry on.
$1 >= $2 # If variable $1 is greater than or equal to variable $2, carry on.
$1 <= $2 # If variable $1 is less than or equal to variable $2, carry on.
$1 eq $2 # If string variable $1 is the same as string variable $2, carry on.
$1 ne $2 # If string variable $1 is NOT the same as string variable $2, carry on.
$1 =~ $2 # If string variable $1 contains/matches the string variable $2, carry on.

In this example, if the user is a smaller level than the mob the mob says "I'm a higher level than you!"

if($ulevel < $mlevel) {
	quest::say("I'm a higher level than you!");
}
if($name ne "Joe") {
	quest::say("I will only talk to joe!");
}

##### **Using $npc->GetHateList();**

sub EVENT\_AGGRO\_SAY {
	if($text=~/hate/i) {
		my @hatelist = $npc->GetHateList();
		foreach $ent (@hatelist) {
			my $h_ent = $ent->GetEnt();  # do not forget GetEnt() or the script halts!
			my $h_dmg = $ent->GetDamage();
			my $h_hate = $ent->GetHate();
			if($h_ent) {
				my $h\_ent\_name = $h_ent->GetCleanName();
				quest::say("$h\_ent\_name is on my hate list with $h\_hate hate and $h\_dmg damage.");
			}
		}
	}
}

#### **Function Lists**

*   Nearly every function for Perl can be found in the EQEmu source[https://github.com/EQEmu/Server/blob/master/zone/perl_mob.cpp](https://github.com/EQEmu/Server/blob/master/zone/perl_mob.cpp) 

#### **Client - $client->Object();**

   AccountID()
   AccountName()
   AddAAPoints(number)
   AddAlternateCurrencyValue(currency_id, value)
   AddCrystals(NumberOfRadiant, NumberOfEbon)
   AddEXP(add_exp, conlevel, resexp)
   AddLevelBasedExp(exp\_percentage, max\_level)
   AddMoneyToPP(copper, silver, gold, platinum, updateclient)
   AddPVPPoints(Points)
   AddSkill(skillid, value)
   Admin()
   AssignTask(taskid, npcid\[, enforce\_level\_requirement\]) # use 0 for npcid to assume current npc, 0/1 to enforce level requirement in DB
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
   DeleteItemInInventory(slot\_id, quantity, client\_update)
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
   GetFactionLevel(char\_id, npc\_id, p\_race, p\_class, p_deity, pFaction, tnpc)
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
   MemSpell(spell\_id, slot, update\_client)
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
   ScribeSpell(spell\_id, slot, update\_client)
   SendColoredText(color, msg)
   SendMarqueeMessage(type, priority, fade\_in, fade\_out,  duration, message) # type = color, priority = text opacity, fade\_in = 1, fade\_out = fade out in MS, duration = duration in MS
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
   SetBindPoint(to\_zone, new\_x, new\_y, new\_z)
   SetCustomItemData()
   SetDeity(i)
   SetDuelTarget(set_id)
   SetDueling(duel)
   SetEXP(set\_exp, set\_aaxp, resexp)
   SetEndurance(Endurance)
   SetFactionLevel(char\_id, npc\_id, char\_class, char\_race, char_deity)
   SetFactionLevel2(char\_id, faction\_id, char\_class, char\_race, char_deity, value)
   SetFeigned(in_feigned)
   SetGM(toggle)
   SetHorseId(horseid_in)
   SetLanguageSkill(langid, value)
   SetMaterial(slot\_id, item\_id)
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
   UpdateTaskActivity(taskID, activityID, count\[, hide update client?\]) # i.e. $client->UpdateTaskActivity(507, 0, 3) will increment task 507's activity 0 by 3.
   UpdateWho(remove)
   UseDiscipline(spell_id, target)
   WorldKick()

#### **Corpse - $corpse->Object();**

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
   SetCash(in\_copper, in\_silver, in\_gold, in\_platinum)
   SetDecayTimer(decaytime)
   Summon(client, spell)
   UnLock()

#### **EntityList - $entity_list->Object();**

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
   MessageStatus(to\_guilddbid, to\_minstatus, type, message, ...)
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
   SignalMobsByNPCID(npc\_type, signal\_id)

#### **Group - $group->Object(); ($group needs to be defined from my $group = $client->GetGroup())**

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

#### **Raid - $raid->Object(); ($raid needs to be defined from my $raid = $client->GetRaid())**

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

#### **Mob - $mob->Object();**

   AddFeignMemory(attacker)
   AddToHateList(other, hate, damage, iYellForHelp, bFrenzy, iBuffTic)
   Attack(other, Hand, FromRiposte)
   BehindMob(other, playerx, playery)
   BuffFadeAll()
   BuffFadeByEffect(effectid, skipslot)
   BuffFadeBySlot(slot, iRecalcBonuses)
   BuffFadeBySpellID(spell_id)
   CalculateDistance(x, y, z)
   CalculateHeadingToTarget(in\_x, in\_y)
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
   CastSpell(spell\_id, target\_id, slot, casttime, mana\_cost, resist\_adjust)
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
   Damage(from, damage, spell\_id, attack\_skill, avoidable, buffslot, iBuffTic)
   DelGlobal(varname)
   Depop(StartSpawnTimer)
   DivineAura()
   DoAnim(animnum, type=1)
   DoArcheryAttackDmg()
   DoKnockback(caster, pushback, pushup)  # $client->DoKnockback($npc, 10, 7) would appear that the NPC knocked the client back
   DoMeleeSkillAttackDmg()
   DoSpecialAttackDamage(target, skill, max\_damage, min\_damage, hate_override)
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
   HealDamage(amount\[, caster\])
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
   Message\_StringID(type, string\_id, distance)
   ModSkillDmgTaken()
   ModVulnerability()
   NPCSpecialAttacks(parse, permtag, reset, remove)
   ProcessSpecialAbilities(str)
   ProjectileAnim(mob, item_id, IsArrow, speed, angle, tilt, arc)
   QuestReward(client, silver, gold, platinum)
   RangedAttack()
   RemoveFromFeignMemory(attacker)
   RemoveNimbusEffect(effectid)
   ResistSpell(resist\_type, spell\_id, caster)
   RogueAssassinate(other)
   Say(format, language_id)
   SendAppearanceEffect(effect1, effect2, effect3, effect4, effect5, specificclient)
   SendIllusion(race, gender, texture, helmtexture, face, hairstyle, haircolor, beard, beardcolor, drakkin\_heritage, drakkin\_tattoo, drakkin_details, size)
   SendPosUpdate(iSendToSelf)
   SendPosition()
   SendTo(new\_x, new\_y, new_z)
   SendToFixZ(new\_x, new\_y, new_z)
   SendWearChange(material_slot)
   SetAllowBeneficial()
   SetAppearance(app, iIgnoreSelf)
   SetBodyType(type, overwrite_orig?)
   SetCurrentWP(waypoint)
   SetDeltas(delta\_x, delta\_y, delta\_z, delta\_h)
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
   SetSlotTint(material\_slot, red\_tint, green\_tint, blue\_tint)
   SetSpecialAbility(ability, value)
   SetSpecialAbilityParam(ability, param, value)
   SetTarget(mob)
   SetTargetDestSteps(target_steps)
   SetTargetable(targetable)
   SetTexture(texture)
   Shout(format, ...)
   SignalClient(client, data)
   SpellEffect(effect, duration, finish\_delay, zone\_wide, unk20, perm\_effect, client) # duration, finish\_delay, zone\_wide, unk20, perm\_effect, and client are Optional.
   SpellFinished(spell\_id, spell\_target, mana_cost)
   Spin()
   StartEnrage()
   Stun(duration) # in whole seconds
   TarGlobal(varname, value, duration, npcid, charid, zoneid)
   TempName(name)
   ThrowingAttack()
   TypesTempPet(typesid, name, duration, follow, target, sticktarg);
   WearChange(material_slot, texture, color)
   WipeHateList()

#### **NPC - $npc->Object();**

   AI_SetRoambox(iDist, iMaxX, iMinX, iMaxY, iMinY, iDelay)
   AddAISpell(priority, spell\_id, type, mana\_cost, recast\_delay, resist\_adjust)
   AddCash(in\_copper, in\_silver, in\_gold, in\_platinum)
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