# EVENT_AGGRO
### Trigger 

- When a mob aggros a client.  

Often used for flavor text--just remember that every NPC_Type has an EmoteID that can often handle this behavior.  

### Example

- In this example, the NPC will say "Time to die PlayerName." when the NPC is aggro'd by the player.

```perl
sub EVENT_AGGRO {
	quest::say("Time to die $name.");
}
```

# EVENT_AGGRO_SAY
### Trigger

- When a mob is targeted, the player types something, and NPC is in combat.

### Exports

| Name | Type | Usage
| --- | --- | ---
|data | int | `quest::say($data); # returns int`
|text | int | `quest::say($text); # returns int`
|langid | int | `quest::say($langid); # returns int`

### Example

- In this example, the NPC, if in combat, would say the names of everyone on its hate list, and include both the amount of damage the entity has done, as well as the amount of hate the entity has generated.

```perl
sub EVENT_AGGRO_SAY {
	#:: Match when a player says "hate", case insensitive because of the /i
	if ($text=~/hate/i) {
	#:: Create an array for all entities on the NPC's hatelist
	my @hatelist = $npc->GetHateList();
		foreach $ent (@hatelist) {
			#:: The entity name
			my $h_ent = $ent->GetEnt();
			#:: The entity's total damanage
			my $h_dmg = $ent->GetDamage();
			#:: The entity's total hate
			my $h_hate = $ent->GetHate();
			#:: Match if entities exist on the hate list
			if ($h_ent) {
				#:: Create a scalar to store the clean name ("Turmoiltoad" vs. "Turmoiltoad001")
				my $h_ent_name = $h_ent->GetCleanName();
				quest::say("$h_ent_name is on my hate list with $h_hate hate and $h_dmg damage.");
			}
		}
    	}
}
```

# EVENT_ATTACK
### Trigger

- When the NPC is attacked.  

Note the subtle difference from EVENT_AGGRO, which is triggered when the NPC is aggro'd (which could occur through bad faction, for instance).

### Example

- In this example, the NPC will say "Time to die PlayerName." when the NPC is attacked by the player.

```perl
sub EVENT_ATTACK {
	quest::say("Time to die $name.");
}
```
# EVENT_AUGMENT_ITEM

### Trigger

- When a client augments an item.  

You would likely use this event in your global player.pl file.

### Example

- In this example, a message in yellow text is displayed to the client when the player adds an augment to an item.

```perl
sub EVENT_AUGMENT_ITEM {
	$client->Message(15, "Yay, it fit!");
}
```

# EVENT_AUGMENT_INSERT

### Trigger

- When a client inserts an augment into an item.  

You would likely use this event in your global player.pl file.

### Example

- In this example, a message in yellow text is displayed to the client when the player puts the augment into the augment slot of an item.

```perl
sub EVENT_AUGMENT_INSERT {
	$client->Message(15, "Yay, it fit!");
}
```

# EVENT_AUGMENT_REMOVE

### Trigger

- When a client removes an augment from an item.  You would likely use this event in your global player.pl file.

### Example

- In this example, a message in yellow text is displayed to the client when the player removes an augment from an item.

```perl
sub EVENT_AUGMENT_ITEM {
	$client->Message(15, "Yay, you pulled it out!");
}
```

# EVENT_CAST

### Trigger

- When a client casts a spell.  

### Exports

|Name | Type | Usage
| --- | --- | ---
|spell_id | int	| `quest::say($spell_id); # returns int`

### Example

- In this example, the player would emote upon a successful cast.  

```perl
sub EVENT_CAST {
	quest::me("regains his concentration and casts his spell.");
}
```

# EVENT_CAST_BEGIN

### Trigger

- When a client begins to cast a spell.

### Exports

|Name | Type | Usage
| --- | --- | ---
|spell_id | int	| `quest::say($spell_id); # returns int`

### Example

- In this example, the player would emote if they begin casting the gate spell.  You would likely place this particular snippet into your global player.pl file.

```perl
sub EVENT_CAST_BEGIN {
	#:: Match if spell is 36 - Gate
	if ($spell_id == 36) {
		quest::me("begins casting the GATE spell");
	}
}
```

# EVENT_CAST_ON

### Trigger

- When a player casts a spell on a player or NPC.

### Exports

|Name | Type | Usage
| --- | --- | ---
|spell_id | int	| `quest::say($spell_id); # returns int`

### Example

- In this example, if the player casts Banish Summoned on an NPC with a Summoned body type, the NPC will be killed. If you were placing this snippet in an NPC's quest script, you likely wouldn't bother matching body type.

```perl
sub EVENT_CAST_ON {
	#:: Match if spell is 116 - Banish Summoned
	if ($spell_id == 116) {
		#:: Match if the NPC's body type is 28 - Summoned Creature
		if ($mob->GetBodyType() == 28) {
			$npc->Kill();
		} 
		else {
			$client->Message(13, "This spell only effects summoned creatures");
		}
	}
}
```

# EVENT_CLICKDOOR

### Trigger

- When the client clicks on a door object.  

Note that you would likely use this event in the zone player.pl file.  Since doors have open types and destination fields stored in the database, most "simple" doors do not require a separate quest script.  An example of a "simple" door would be any door that requires a single keyitem (by Item ID) to open, like the door to the basement in Befallen.

### Exports

|Name | Type | Usage
| --- | --- | ---
|doorid | int	| `quest::say($doorid); # returns int`
|version | int	| `quest::say($version); # returns int`

### Example

- In this example, a player who is part of a Deepest Guk Adventure would be teleported to Deepest Guk when they click the doorway found in the Hollow Log.

```perl
sub EVENT_CLICKDOOR {
	#:: Match if doorID is 1 - the door found in the Hollow Log that leads to Deepest Guk Adventures
	if ($doorid == 1) {
		#:: Create a variable to store the player's adventure zone instance ID
		$GukAInstance = quest::GetInstanceID("guka",50);
		#:: Match if the player has an instance
		if ($GukAInstance > 0) {
			#:: Teleport the player to their instance in Deepest Guk at the safe spot
			quest::MovePCInstance(229, $GukAInstance, 101, -841, 2.38);
		} 
		else {
			$client->Message(13, "You are not a part of a Deepest Guk adventure instance!");
		}
	}
}
```


# EVENT_CLICK_OBJECT

### Trigger

- When the client clicks on an object.  

Note the similarity between this event and Perl EVENT_CLICKDOOR, since it is easy to confuse a door object (like a Plane of Knowledge Book) with Objects (IE Pottery wheels, Brew Barrels, etc.).  You would likely use this event in the zone player.pl (or global_player.pl) files.

### Exports

|Name | Type | Usage
| --- | --- | ---
|objectid | int	| `quest::say($objectid); # returns int`
|clicker_id | int	| `quest::say($clicker_id); # returns int`

### Example

- In this example, a message is displayed to a player when they open the Ogre Cultural Forge in Oggok.

```perl
sub EVENT_CLICK_OBJECT {
        #:: Match to the ogre cultural forge in Oggok by object ID
        if ($objectid == 1075) {
                #:: Check to see if the player who clicked is a race other than Ogre
                if ($race ne "Ogre") {
                        #:: Send the client a message in color 1 (gray)
                        $client->Message(1,"The foul stench of Ogre overwhelms you as you open the forge.");
                }
                else {
                        $client->Message(1,"Mmmm--dis smells just like home.");
                }
        }
}
```

# EVENT_COMBAT

### Trigger

- When an NPC enters or leaves combat.

### Example

- In this example, the NPC will say some flavor text when entering combat.

```perl
sub EVENT_COMBAT {
	#:: combat state 1 = True
	if ($combat_state == 1) {
		quest::say("Time to die $name!");
	}
}
```

# EVENT_COMBINE_FAILURE

### Trigger

- When a combine is unsuccessful.  You would likely use this event in your global / player.pl file.

### Exports

| Name | Type | Usage
| --- | --- | --- |
|recipe_id | int | `quest::say($recipe_id); # returns int`
|recipe_name | int | `quest::say($recipe_name); # returns int`

### Example

- In this example, we watch for a player failing the combine for a Hand Made Backpack and then tease them.

```perl
sub EVENT_COMBINE_FAILURE {
	#:: Match Recipe 2686: "Hand Made Backpack" by ID
	if ($recipe_id == 2686) {
		#:: Send the client a message in color 15 (yellow)
		$client->Message(15,"Awww...now where are you going to put all of your stuff?");
	}
}
```

# EVENT_COMBINE_SUCCESS

### Trigger

- When a combine is successful.

### Exports

| Name | Type | Usage
| --- | --- | --- |
|recipe_id | int | `quest::say($recipe_id); # returns int`
|recipe_name | int | `quest::say($recipe_name); # returns int`

### Example

- In this example, we send the client a message when they successfully combine a Hand Made Backpack

```perl
sub EVENT_COMBINE_SUCCESS {
	#:: Match Recipe 2686: "Hand Made Backpack" by ID
	if ($recipe_id == 2686) {
		#:: Send the client a message in color 15 (yellow)
		$client->Message(15,"Yay, now you have a place to put all of your stuff!");
	}
}
```

# EVENT_COMMAND

### Trigger

- When a player says anything like a command.  Replaced/Synonymous with [EVENT_SAY](https://github.com/EQEmu/Server/wiki/Perl-API---Perl-Sub-Event-Examples#event_say).

# EVENT_CONNECT

### Trigger

- when a player connects to the world.

You would likely be using this event in your global_player.pl.

### Example

- In this example, veteran AAs are awarded based on accumulated play time.

```perl
sub EVENT_CONNECT {
	my %vet_aa = (481 => [31536000, 1, 1],
	482 => [63072000, 1, 1],
	483 => [94608000, 1, 1],
	484 => [126144000, 1, 1],
	485 => [157680000, 1, 1],
	486 => [189216000, 1, 1],
	487 => [220752000, 1, 1],
	511 => [252288000, 1, 1],
	2000 => [283824000, 1, 1],
	8081 => [315360000, 1, 1],
	8130 => [346896000, 1, 1],
	453 => [378432000, 1, 1],
	182 => [409968000, 1, 1],
	600 => [441504000, 1, 1]);
	foreach my $key (keys %vet_aa) {
		if ($vet_aa{$key}[2] && ($vet_aa{$key}[2] || $client->GetAccountAge() >= $vet_aa{$key}[0])) {
			$client->GrantAlternateAdvancementAbility($key, 1);
		}
	}
}
```

# EVENT_DEATH

### Trigger

- When the NPC dies. Fires before death finishes.

### Exports

| Name | Type | Details
| --- | --- | --- 
| client | client | client who killed mob
| npc | npc | npc that was killed
| killer_id | int | client ID of killer. (Does not seem castable to mob)
| killer_damage | int | How much damage was dealt on killing blow
| killer_spell | int | Spell ID used to kill mob
| killer_skill | int | Skill ID used to kill mob
| charid | int | Character ID who killed mob
| class | string | Class Name who killed mob
| faction | int | Faction comparison of killed mob vs killer
| h | float | heading of mob during death
| hpratio | float | percent health of mob after death (negative value)
| mlevel | int | level of mob killed
| mname | string | name of mob killed
| mobid | int | id of mob killed
| name | string | name of killer
| race | string | race of killer
| status | int | account status of killer
| uguild_id | int | uguild of killer
| ulevel | int | level of killer
| userid | int | user id of killer
| x | float | x position of killed mob
| y | float | y position of killed mob
| z | float | z position of killed mob
| zonehour | int | hour of zone when mob died
| zoneid | int | zone id where mob died
| zoneln | string | long name of zone where mob died
| zonemin | int | minimum level to enter zone where mob died
| zonesn | string | short name of zone where mob died
| zonetime | int | time of zone where mob died
| zoneweather | int | 

# EVENT_DEATH_COMPLETE

### Trigger

- when the NPC dies.

# EVENT_DESTROY_ITEM

### Trigger

- when a client destroys an item.

# EVENT_DISCONNECT

### Trigger

- when a player disconnects from the world.

# EVENT_DISCOVER_ITEM

### Trigger

- when an item is discovered.

# EVENT_DROP_ITEM

### Trigger

- when a client drops an item.

# EVENT_DUEL_LOSE

### Trigger

- when a client loses a duel.

You would use this event in the global global_player.pl file.

### Example

- In this example, we set a quest global to keep track of a player's dueling failures.

```perl
sub EVENT_DUEL_LOSE {
	#:: Match if the player has a qglobal for duelslost
	if (!defined $qglobals{"duelslost"}) {
		#:: If no qglobal exists, set one
		quest::setglobal("duelslost",1,5,"F");
	}
	else {
		#:: If the qglobal exists, iterate the count up one
		quest::setglobal("duelslost",$qglobals{"duelslost"}+1,5,"F");
	}
}
```

# EVENT_DUEL_WIN

### Trigger

- when a client wins a duel.

You would use this event in the global global_player.pl file.

### Example

- In this example, we set a quest global to keep track of a player's dueling wins.

```perl
sub EVENT_DUEL_WIN {
	#:: Match if the player has a qglobal for duelswon
	if (!defined $qglobals{"duelswon"}) {
		#:: If no qglobal exists, set one
		quest::setglobal("duelswon",1,5,"F");
	}
	else {
		#:: If the qglobal exists, iterate the count up one
		quest::setglobal("duelswon",$qglobals{"duelswon"}+1,5,"F");
	}
}
```

# EVENT_ENTER

### Trigger

- When a client enters a mob's proximity (as defined by quest::set_proximity(min_x, max_x, min_y, max_y, min_z, max_z)).

### Example

- In this example, we first set the NPC's proximity; when a player enters the proximity, they become PVP (red).

```perl
sub EVENT_SPAWN {
	#:: Set the proximity bounds around the NPC on spawn, 200 units across
	$x = $npc->GetX();
	$y = $npc->GetY();
	quest::set_proximity($x - 100, $x + 100, $y - 100, $y + 100);
}

sub EVENT_ENTER {
	#:: Turn pvp on
	quest::pvp(on);
}
```

# EVENT_ENTER_AREA

### Trigger

- when a client enters the area of a mob.

# EVENT_ENTERZONE

### Trigger

- When a player enters the zone.  Likely you will add to the zone player.pl file.

### Example

- In this example we remove the LDON compass mark.

```perl
sub EVENT_ENTERZONE {
	#:: Clear the LDON Compass mark
	$client->ClearCompassMark();
}
```

- In this example we create a LDON compass mark

```perl
sub EVENT_ENTERZONE {
	#:: Create a scalar for storing the instance ID
	$RujDInstance = quest::GetInstanceID("rujd",50);
	#:: If the instance ID exists, it should be greater than 0--mark the player's compass if it is
	if ($RujDInstance > 0) {
		#:: Create a line on the compass leading the player to X,Y,Z
		$client->MarkCompassLoc(-157.09, 19.31, 100);
	}
}
```

# EVENT_EQUIP_ITEM

### Trigger

- When a player equips an item.

# EVENT_EXIT

### Trigger

- by any client who leaves a mob's proximity (as defined by quest::set_proximity).

### Example

- In this example, we first set the NPC's proximity; when a player exits the proximity, they are no longer PVP (blue).

### Example

```perl
sub EVENT_SPAWN {
	#:: Set the proximity bounds around the NPC on spawn, 200 units across
	$x = $npc->GetX();
	$y = $npc->GetY();
	quest::set_proximity($x - 100, $x + 100, $y - 100, $y + 100);
}

sub EVENT_EXIT {
	#:: Turn pvp off
	quest::pvp(off);
}
```

# EVENT_FEIGN_DEATH

### Trigger

- When a client feigns death.

### Example

```perl
sub EVENT_FEIGN_DEATH {
	#:: See if the player has a pet
	if ($client->GetPetID()) {
		#:: Identify the pet by ID and kill it
		$PetID = $entity_list->GetMobByID($client->GetPetID());
		$PetID->Kill();
	}
}
```

# EVENT_FISH_FAILURE

### Trigger

- When a client fails at fishing.

You would use this event in the zone player.pl file.

### Example

- In this example, a message is displayed by the client if fishing is unsuccessful.

```perl
sub EVENT_FISH_FAILURE {	
	$client->Message(1, "Maybe you're using the wrong bait!")
}
```

# EVENT_FISH_START

### Trigger

- when a client starts fishing.

You would use this event in the zone player.pl file.

### Example

- In this example, a message is displayed by the client if they start fishing.  

```perl
sub EVENT_FISH_START {
	$client->Message(1, "You crack a beer and toss your line in.");
}
```

# EVENT_FISH_SUCCESS

### Trigger

- when a client succeeds at fishing.

You would use this event in the zone player.pl file or the global global_player.pl file.

### Exports

|Name | Type | Usage
| --- | --- | ---
|fished_item | int | `quest::say($fished_item); # returns int`

### Example

- In this example, we set a quest global to keep track of a player's fishing successes.
- You would use this event in the global global_player.pl file.

```perl
sub EVENT_FISH_SUCCESS {
	#:: Match if the player has a qglobal for fishsuccess
	if (!defined $qglobals{"fishsuccesses"}) {
		#:: If no qglobal exists, set one
		quest::setglobal("fishsuccesses",1,5,"F");
	}
	else {
		#:: If the qglobal exists, iterate the count up one
		quest::setglobal("fishsuccesses",$qglobals{"fishsuccesses"}+1,5,"F");
	}
}
```

# EVENT_FORAGE_FAILURE

### Trigger

- When a client fails at foraging.

You would use this event in the zone player.pl or global global_player.pl file.

### Example

- In this example, we set a quest global to keep track of a player's foraging failures.

```perl
sub EVENT_FORAGE_FAILURE {
	#:: Match if the player has a qglobal for foragefails
	if (!defined $qglobals{"foragefails"}) {
		#:: If no qglobal exists, set one
		quest::setglobal("foragefails",1,5,"F");
	}
	else {
		#:: If the qglobal exists, iterate the count up one
		quest::setglobal("foragefails",$qglobals{"foragefails"}+1,5,"F");
	}
}
```

# EVENT_FORAGE_SUCCESS

### Trigger

- when a client succeeds at foraging.

You would use this event in the global global_player.pl file.

### Example

- In this example, we set a quest global to keep track of a player's foraging successes.

```perl
sub EVENT_FORAGE_SUCCESS {
	#:: Match if the player has a qglobal for foragesuccess
	if (!defined $qglobals{"foragesuccesses"}) {
		#:: If no qglobal exists, set one
		quest::setglobal("foragesuccesses",1,5,"F");
	}
	else {
		#:: If the qglobal exists, iterate the count up one
		quest::setglobal("foragesuccesses",$qglobals{"foragesuccesses"}+1,5,"F");
	}
}
```

# EVENT_GROUP_CHANGE

### Trigger

- when a group change occurs.

# EVENT_HATE_LIST

### Trigger

- When a mob's hate list is changed.

### Example

In this example, some flavor text is added as a player is added and removed from the NPC's hate list.

```perl
sub EVENT_HATE_LIST {
	if ($hate_state == 1) {
		quest::say("$name is gonna die!");
	}
	if ($hate_state == 0) {
		quest::say("$name is no match for my might!");
	}
}
```

# EVENT_HP

### Trigger

- When a mob's HP dropping below a threshold (as defined by quest::setnexthpevent()).

### Example

- In this example, we set the HP event threshold, and then depop the mob when the threshold is reached.

```perl
sub EVENT_SPAWN {
	#:: Set the HP event threshold for 50 percent health
	quest::setnexthpevent(50);
}

sub EVENT_HP {
	#:: Match when the threshold is met
	if ($hpevent == 50) {
		quest::depop();
	}
}
```

# EVENT_ITEM

### Trigger

- When an item or money is turned into the mob.

### Example

- In this example, we turn in 3250 gold, a Ring of the Ancients, and a Shadowed Rapier in exchange for our Journeyman's Boots

```perl
sub EVENT_ITEM {
	#:: Create a scalar variable to store cash--only gold and platinum
	my $cash = (($platinum * 10) + $gold);
 	#:: Match if the cash is 3250gp or more
	if ($cash >= 3250) {
		#:: Match turn for 12268 - Ring of the Ancients and 7100 - Shadowed Rapier
		if (plugin::check_handin(\%itemcount, 12268 => 1, 7100 => 1)) {
			quest::say("The time to trade has come!! I am now rich and you are now fast. Take the Journeyman Boots and run like the wind.");
			#:: Give a 2300 - Journeyman's Boots
			quest::summonitem(2300);
			#:: Play the ding sound
			quest::ding();
			#:: Grant a small amount of experience
			quest::exp(1250);
      		}
	}
	else {
		#:: Return unused coin
		quest::givecash(0, 0, $gold, $platinum);
	}
	#:: Return unused items
	plugin::return_items(\%itemcount);
} 
```

# EVENT_ITEM_CLICK

### Trigger

- When an item is clicked.

This is a useful script to put in the Global quest scripts directory, so that you can make an item click work anywhere in the world.

### Exports

| Name | Type | Usage
| --- | --- | --- 
| itemid | int | `quest::say($itemid); # returns int`
| itemname | int | `quest::say($itemname); # returns int`
| slotid | int | `quest::say($slotid); # returns int`
| spell_id | int | `quest::say($spell_id); # returns int`

### Example

- This example is taken from the Evil Eye Costume Kit, which is part of the Halloween Costume illusion items.
- Note that the scriptfileid field for the item is set to 30073 in the database.
- Note that a corresponding quest file exists at global/items/script_30073.pl.

```perl
sub EVENT_ITEM_CLICK {
	#::: Use == for numeric comparison to Item ID 54711 - Evil Eye Costume Kit
	if ($itemid == 54711) {
		#::: Change the player's race to 469 - Evil Eye
		quest::playerrace(469);
	} 
}
```

# EVENT_ITEM_CLICK_CAST

### Trigger

- When a client casts the click effect on an item.

### Exports

| Name | Type | Usage
| --- | --- | --- 
| itemid | int | `quest::say($itemid); # returns int`
| itemname | int | `quest::say($itemname); # returns int`
| slotid | int | `quest::say($slotid); # returns int`
| spell_id | int | `quest::say($spell_id); # returns int`

# EVENT_ITEM_ENTER_ZONE
Called when an item that would trigger EVENT_SCALE_CALC is in the inventory when a player zones in.

# EVENT_ITEM_TICK

### Trigger

- when the click effect of an item ticks.

# EVENT_KILLED_MERIT

### Trigger

- on NPC death and applies to the group that did the most damage to the NPC (IE the group that got XP for the kill, assuming there was XP; or the group that gets loot rights to the NPC, assuming that there was loot). Although not often used, this event gives you the opportunity to assign quest globals (for character flags) or update tasks.

### Example

```perl
sub EVENT_KILLED_MERIT {
	#:: Get the name of the mob to use in the quest global
	my $slain = $npc->GetCleanName();
	#:: Set the quest global--this would apply to all group members
	$client->SetGlobal($slain,1,5,"F");
	#:: Display an emote message to each client in yellow to notify them that they received credit
	$client->Message(15, "You have received credit for killing ".$slain.".");
}
```

# EVENT_LEAVE_AREA

### Trigger

- when a client leaves a mob's area.

# EVENT_LEVEL_UP

### Trigger

- when the player gains a level.

# EVENT_LOOT

### Trigger

- when player successfully loots an item from a corpse.

### Exports

|Name | Type | Usage
| --- | --- | ---
|looted_id | int | `quest::say($looted_id); # returns int`
|looted_charges | int | `quest::say($looted_charges); # returns int`
|corpse | int | `quest::say($corpse); # returns int`

### Example

- This example uses the loot event to match a particular item and corpse.

Note that we use the NPC's name (Fippy_Darkpaw) and not the numeric corpse ID (IE 249) or full corpse name (IE Fippy_Darkpaw`s_corpse249).

```perl
sub EVENT_LOOT {
	#::: Use == for numeric comparison to Item ID 60396 - Fippy's Paw
	#::: Use eq for string comparison to Fippy_Darkpaw's corpse
	if ($looted_id == 60396 && $corpse eq "Fippy_Darkpaw") {
		$client->Message(15, "The bloody stump of Fippy's paw--it's a lot smaller than you thought it would be.");
	}
}
```

# EVENT_NPC_SLAY

### Trigger

- When an NPC slays another NPC.

### Example

- In this example, we add some flavor text when the Exterminator kills the rats.

```perl
sub EVENT_NPC_SLAY {
	quest::say("Another unworthy opponent. Never cross Mining Guild 628!!");
}
```

# EVENT_PLAYER_PICKUP

### Trigger

- When a player picks up an object from the ground.  You would likely use this event in your zone player.pl file.

### Example

-- In this example, when the player picks up a Chalice of Conquest, a signal is sent to another NPC

```perl
#:: Chalice of Conquest quest
sub EVENT_PLAYER_PICKUP {
	#:: Match 12274 - Chalice of Conquest, ground spawn created by #Captain_Klunga.pl
	if ($picked_up_id == 12274) {
		#:: Send a signal to Dagnor's Cauldron >> #Captain_Klunga (70072)
		quest::signal(70072,1);
	}
}
```

# EVENT_POPUPRESPONSE
Used with quest::popup.

# EVENT_PROXIMITY_SAY

### Trigger

- When the client enters a mob's proximity and uses the appropriate text trigger supplied beneath this event Note that you must set quest::enable_proximity_say() and quest::set_proximity().

### Example

- In this example, we establish a proximity around the NPC and enable the NPC to listen for say messages in the proximity (IE without having the mob targeted, necessarily); we then match for a "hail" message and attack anyone foolish enough to say hello.

```perl
sub EVENT_SPAWN {
	#:: Set the proximity bounds around the NPC on spawn, 30 units across
	$x = $npc->GetX();
	$y = $npc->GetY();
	quest::set_proximity($x-15,$x+15,$y-15,$y+15);
	#:: Enable the NPC for proximity say
	quest::enable_proximity_say();
}

sub EVENT_SAY {
	#:: Match say message for "hail", /i for case insensitive
	if ($text=~/hail/i) {
		#:: Attack whoever hailed the NPC
		quest::attack($name);
	}
}
```

# EVENT_RESPAWN

### Trigger

- on respawn

### Exports

|Name | Type | Usage
|option | int | `quest::say($option); # returns int`
|resurrect | int | `quest::say($resurrect); # returns int`

# EVENT_SAY

### Trigger

- when a mob is targeted and the player types something.

### Exports

| Name | Type | Details
| --- | --- | ---
| client | client | Client who did say event
| npc | npc | Npc who is handling say event
| charid | int | character id of who did say event
| class | string | class of who did say event
| data | int | unknown? 124078
| faction | int | faction comparison of who did say and npc
| h | float | heading position of npc
| hpratio | float | hp ratio e.g. 100
| instanceid | int | instance id of zone, typically 0
| instanceversion | int | instance version of zone, typically 0
| langid | int | language id, common is 0
| mlevel | int | mob level of npc
| mname | string | mob name of npc
| mobid | int | mob entity id of npc
| name | string | name of who did say event
| race | string | race of who did say event
| status | int | account status of who did say event
| text | string | Text of who did say event
| uguild_id | int | guild id of who did say event
| uguildrank | int | guild rank of who did say event
| ulevel | int | level of who did say event
| userid | int | user id of who did say event
| x | float | x position of npc
| y | float | y position of npc
| z | float | z position of npc
| zonehour | int | hour of zone when mob died
| zoneid | int | zone id where mob died
| zoneln | string | long name of zone where mob died
| zonemin | int | minimum level to enter zone where mob died
| zonesn | string | short name of zone where mob died
| zonetime | int | time of zone where mob died
| zoneweather | int | weather of zone where mob died

### Example

- This example is a response to a "hail"

```perl
sub EVENT_SAY {
     #::: Checks if the text is like "Hail", the "/i" is for case-insensitive.
     if ($text=~/Hail/i) {
          quest::say("Hello, $name!");
     }
}
```

- This example additionally checks the language of the "hail", and will only respond to text in that language.

```perl
sub EVENT_SAY {
     #::: Checks to see if the language is Thieves Cant (language ID 10)
     if ($langid == 10) {
          #::: Checks if the text is like "Hail", the "i" is for case-insensitive.
          if ($text=~/Hail/i) {
               # Respond, using the same language
               quest::say("Hello, $name!",10);
          }
     }
}
```

# EVENT_SCALE_CALC

### Trigger

- when an item is equipped to scale the item.

# EVENT_SIGNAL

### Trigger

- Triggered using quest::signal(NPC_ID,wait_time) or quest::signalwith(NPC_ID,signal_ID,wait_time).

Generally a way to have one NPC cause another NPC to do something.  Often used with "controller" NPCs that coordinate events.

### Exports

|Name | Type | Usage
| --- | --- | ---
|signal | int | `quest::say($signal); # returns int`

### Example

- This example increments a counter each time a signal with the appropriate ID is received.

```perl
my $count = 0;

sub EVENT_SIGNAL {
     #::: Signal 1 is from the clockwork spiders being killed.
     if ($signal == 1) {
          $count++;
          if ($count == 1) {
               #::: Start a three minute timer to spawn targetable Manaetic Behemoth
               quest::settimer("wake", 180);
          }
     }
     #::: Signal 2 is from the clockwork spiders reaching Manaetic Behemoth.
     if ($signal == 2) {
          #::: Reset the count and make them start over.
          $count = 0;
          quest::stoptimer("wake");
     }
}

sub EVENT_TIMER {
     #::: This uses eq for a string comparison to match the timer "wake".
     #::: Check the count to make sure the clockwork spiders were killed and not just kited. 
     if ($timer eq "wake" && $count >= 12) {
          quest::stoptimer("wake");
          #::: Spawn the targetable version of Manaetic Behemoth in place
          quest::spawn2(206074,0,0,$x,$y,$z,0);
          #::: Depop the untargetable version of Manaetic Behemoth with respawn timer active.
          quest::depop_withtimer();
     }
}
```

# EVENT_SLAY

### Trigger

- whenever an NPC kills a player.  

Often this event is used for some flavor messages, or to spawn adds. Do not confuse this event with EVENT_DEATH_COMPLETE or EVENT_DEATH, which are used when a player kills an NPC.

### Example

- This is a well-known example from Emperor Ssraeshza, who mocks any player that he kills

```perl
sub EVENT_SLAY {
	quest::say("Your god has found you lacking.");
}
```

# EVENT_SPAWN

### Trigger

- When the NPC spawns.

This event is often used to start timers, attack player targets, establish NPC HP events or proximities, start dialogues, and more.

### Example

- In this example, when the mob spawn, we make it run and attack a nearby player while it shouts a war cry.

```perl
sub EVENT_SPAWN {
	#:: Set the NPC to run
	quest::SetRunning(1);
	#:: Shout out a war cray
	quest::shout("For Jotenheimr!!!");
	#:: Try to find a random client within 200 units of the NPC
	my $rClient = $entity_list->GetRandomClient($x,$y,$z, 200);
	#:: If there's a random sucker nearby, attack them
	if ($rClient) {
		quest::attack($rClient->GetName());
	}
}
```

# EVENT_SPELL_EFFECT_CLIENT

### Trigger

- when the spell lands on a client.

# EVENT_SPELL_EFFECT_NPC

### Trigger

- when the spell lands on an NPC.

# EVENT_SPELL_BUFF_TIC_CLIENT

### Trigger

- when the spell ticks on a client.

# EVENT_SPELL_BUFF_TIC_NPC

### Trigger

- when the spell ticks on an NPC.

# EVENT_SPELL_EFFECT_TRANSLOCATE_COMPLETE

### Trigger

- when translocation is complete.

# EVENT_SPELL_FADE

### Trigger

- when a spell fades.

# EVENT_TARGET_CHANGE

### Trigger

- when a mob changes their current target or clears it.

# EVENT_TASKACCEPTED

### Trigger

- when a player accepts a task from the task selector window.

Typically you would handle this functionality using the task system.

# EVENT_TASK_COMPLETE

### Trigger

- when a player completes a task.

Typically you would handle this functionality using the task system.

# EVENT_TASK_FAIL

### Trigger

- when a player fails a task.

Typically you would handle this functionality using the task system.

# EVENT_TASK_STAGE_COMPLETE

### Trigger

- When a task stage is completed.

Typically you would handle this functionality using the task system.

### Example

- In this example, when a player completes a task, it triggers the event and tries to match with task ID 212; if it matches, a yellow message is displayed to the client.

```perl
sub EVENT_TASK_STAGE_COMPLETE {
	#:: Match task id 212
	if ($task_id == 212) {
		$client->Message(15,"The zombie presence seems somewhat lessened, and perhaps they have been quelled...for the time being.");
	}
}
```

# EVENT_TASK_UPDATE

### Trigger

- when a player's task is updated.

# EVENT_TIMER

### Trigger

- by a quest::settimer(timer_name,duration_in_seconds) or quest::settimerMS(timer_name,duration_in_milliseconds)

The timer will loop until it is stopped, and EVENT_TIMER will trigger each time that the duration of the timer elapses.  Timers can be stopped using the quest::stopalltimers() or quest::stoptimer(timer_name) functions.

### Exports

|Name | Type | Usage
|timer | int | `quest::say($timer); # returns int`

### Example

- This is an example of using a timer with a string name to cause an NPC to depop 30 minutes after it spawns

```perl
sub EVENT_SPAWN {
     # Start a timer that is named "depop", the duration is 1,800 seconds (30 minutes)
     quest::settimer("depop",1800); 
}

sub EVENT_TIMER {
     # Use eq for string comparison to match timer "depop"
     if ($timer eq "depop") {
          # Stop timer "depop" from looping
          quest::stoptimer("depop"); 
          quest::depop(); 
     }
}
```

# EVENT_TRADE

### Trigger

- by beginning a trade.

# EVENT_UNAUGMENT_ITEM

### Trigger

- when a client removes an augment from an item.

# EVENT_UNEQUIP_ITEM

### Trigger

- when a client unequips an item.

# EVENT_WAYPOINT_ARRIVE

### Trigger

- When an NPC arrives at a grid waypoint entry.

### Exports 

|Name | Type | Description
| --- | --- | ---
|wp | int | `quest::say($wp); # returns int`

### Example

- This example would cause your NPC to speak as it arrives at a particular waypoint.
- Don't forget to count waypoint 0 (the spawn point) when using waypoint events.

```perl
sub EVENT_WAYPOINT_Arrive {
     # If we have arrived at waypoint 10
     if ($wp == 10) {
          quest::say("We're finally here!");
     }
}
```

# EVENT_WAYPOINT_DEPART

### Trigger

- When an NPC leaves its current grid waypoint entry.

### Exports 

|Name | Type | Description
| --- | --- | ---
|wp | int | `quest::say($wp); # returns int`

### Example

- This example would cause your NPC to speak as it departs a particular waypoint.
- Don't forget to count waypoint 0 (the spawn point) when using waypoint events.

```perl
sub EVENT_WAYPOINT_DEPART {
     # If we departed waypoint 0
     if ($wp == 0) {
          quest::say("And we're off!");
     }
}
```

# EVENT_WEAPON_PROC

### Trigger

- when a weapon procs.

# EVENT_ZONE

### Trigger

- When a player leaves a zone.

### Example

- In this example, we blow up pets when a player with a pet zones.

```perl
sub EVENT_ZONE {
	#:: Match if a player has a pet
	if ($client->GetPetID()) {
		#:: Get the pet's ID and kill it
		$PetID = $entity_list->GetMobByID($client->GetPetID());
		$PetID->Kill();
	}	
}
```