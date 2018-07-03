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

# EVENT_DUEL_WIN

### Trigger

- when a client wins a duel.

# EVENT_ENTER

### Trigger

- When a client enters a mob's proximity (as defined by quest::set_proximity).

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

```perl
sub EVENT_ENTERZONE {
	#:: Clear the LDON Compass mark
	$client->ClearCompassMark();
}
```

# EVENT_EQUIP_ITEM

### Trigger

- when a player equips an item.

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

- when a client feign death.

# EVENT_FISH_FAILURE

### Trigger

- When a client fails at fishing.

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

# EVENT_FORAGE_FAILURE

### Trigger

- when a client fails at foraging.

# EVENT_FORAGE_SUCCESS

### Trigger

- when a client succeeds at foraging.

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

- when an item is clicked.

# EVENT_ITEM_CLICK_CAST

### Trigger

- when a client casts the click effect on an item.

# EVENT_ITEM_ENTER_ZONE
Called when an item that would trigger EVENT_SCALE_CALC is in the inventory when a player zones in.

# EVENT_ITEM_TICK

### Trigger

- when the click effect of an item ticks.

# EVENT_KILLED_MERIT

### Trigger

- on NPC death when a client is in a group credited with doing the most damage to said loot table NPC.

# EVENT_LEAVE_AREA

### Trigger

- when a client leaves a mob's area.

# EVENT_LEVEL_UP

### Trigger

- when the player gains a level.

# EVENT_LOOT

### Trigger

- when player successfully loots an item from a corpse.

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

# EVENT_SAY

### Trigger

- when a mob is targeted and the player types something.

# EVENT_SCALE_CALC

### Trigger

- when an item is equipped to scale the item.

# EVENT_SIGNAL

### Trigger

- by a call to quest::signal() or quest::signalwith().

# EVENT_SLAY

### Trigger

- whenever an NPC kills someone.

# EVENT_SPAWN

### Trigger

- when the NPC spawns.

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

# EVENT_TASK_COMPLETE

### Trigger

- when a player completes a task.

# EVENT_TASK_FAIL

### Trigger

- when a player fails a task.

# EVENT_TASK_STAGE_COMPLETE

### Trigger

- when a task stage is completed.

# EVENT_TASK_UPDATE

### Trigger

- when a player's task is updated.

# EVENT_TIMER

### Trigger

- by a quest::settimer().

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

- when a mob arrives at a waypoint.

# EVENT_WAYPOINT_DEPART

### Trigger

- when a mob leaves a waypoint.

# EVENT_WEAPON_PROC

### Trigger

- when a weapon procs.

# EVENT_ZONE

### Trigger

- when a player zones.