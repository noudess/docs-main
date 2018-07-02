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

- When the NPC is attacked.  Note the subtle difference from EVENT_AGGRO, which is triggered when the NPC is aggro'd (which could occur through bad faction, for instance).

### Example

- In this example, the NPC will say "Time to die PlayerName." when the NPC is attacked by the player.

```perl
sub EVENT_ATTACK {

	quest::say("Time to die $name.");
}
```
# EVENT_AUGMENT_ITEM

### Trigger

- When a client augments an item.  You would likely use this event in your global player.pl file.

### Example

- In this example, a message in yellow text is displayed to the client when the player adds an augment to an item.

```perl
sub EVENT_AUGMENT_ITEM {

	$client->Message(15, "Yay, it fit!");
}
```

# EVENT_AUGMENT_INSERT

### Trigger

- When a client inserts an augment into an item.  You would likely use this event in your global player.pl file.

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

- When the client clicks on a door object.  Note that you would likely use this event in the zone player.pl file.

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

- when a combine is unsuccessful.

# EVENT_COMBINE_SUCCESS

### Trigger

- when a combine is successful.

# EVENT_COMMAND

### Trigger

- When a player says anything like a command.  Replaced/Synonymous with EVENT_SAY.

# EVENT_CONNECT

### Trigger

- when a player connects to the world.

# EVENT_DEATH

### Trigger

- when the NPC dies. Fires before death finishes.

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

- by any client who enters a mob's proximity.

# EVENT_ENTER_AREA

### Trigger

- when a client enters the area of a mob.

# EVENT_ENTERZONE

### Trigger

- when a player enters the zone.

# EVENT_EQUIP_ITEM

### Trigger

- when a player equips an item.

# EVENT_EXIT

### Trigger

- by any client who leaves a mob's proximity.

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

- when a mob's hate list is changed.

# EVENT_HP

### Trigger

- by a mob's HP dropping below a threshold.

# EVENT_ITEM

### Trigger

- when an item or money is turned into the mob.

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

- when an NPC slays another NPC.

# EVENT_PLAYER_PICKUP

### Trigger

- when a player picks up an object from the ground.

# EVENT_POPUPRESPONSE
Used with quest::popup.

# EVENT_PROXIMITY_SAY

### Trigger

- if the client enters a mob's proximity and uses the appropriate text trigger supplied beneath this event. (set quest::enable_proximity_say() and param 7 in q:set_prox)

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