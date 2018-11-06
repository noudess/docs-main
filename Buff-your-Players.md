Below are some examples of quest scripts for NPCs that can buff your players.  These scripts would go in your quest scripts directory, and would be named appropriately based on the NPC that you will create to buff your players.

# Discipline Trainer (PERL)

* File Name (example): Dave_the_Disciplinarian.pl
* Description:  This script will train all available disciplines up to the player's current level.

```perl
sub EVENT_SAY {
	#:: Match text for "hail", case insensitive
	if ($text=~/hail/i) {
		#:: Send a message that only the client can see, in yellow (15) text
		$client->Message(15, "With just one look, I can see that you have forgotten the finer points of combat, $name.  Would you like me to [" . quest::saylink("teach") . "] you how to perform the skills that require more discipline than the basics?");
	}
	#:: Match text for "teach", case insensitive
	elsif ($text=~/teach/i) {
		#:: Clear out any existing disciplines (optional)
		quest::untraindiscs();
		#:: Train all disciplines up to the user's level
		quest::traindiscs($ulevel, 0);
		#:: Send a message that only the client can see, in yellow (15) text
		$client->Message(15, "You look like a more fierce combatant already! Go out and test your new abilities!");
		#:: Play a Ding! sound
		quest::ding();
	}
}

sub EVENT_ITEM {
	#:: Return unused items since we don't expect any handins
	plugin::returnUnusedItems();
}
```

If you would prefer that your players do not have to interact with an NPC, it is quite simple to add all new disciplines each time a player levels using a perl script:

* File Name: global/global_player.pl (add this code to the existing script file)
* Description:  This script will train all new disciplines when a player levels up.

```perl
sub EVENT_LEVEL_UP {
	#:: Train all disciplines, maximum set to player's level, minimum set to the level prior
	quest::traindiscs($ulevel,$ulevel - 1);
}
```


# Spell Scriber (PERL)

* File Name (example): Skippy_the_Scribe.pl
* Description:  This script will scribe all available spells (or songs) up to the player's current level.

```perl
sub EVENT_SAY {
	#:: Match text for "hail", case insensitive
	if ($text=~/hail/i) {
		#:: Separate response for melee classes--match classes using a string comparison (eq)
		if ($class eq 'Berserker' || $class eq 'Monk' || $class eq 'Rogue' || $class eq 'Warrior') {
			#:: Send a message that only the client can see, in yellow (15) text
			$client->Message(15, "Young fighter, I am the greatest spell scribe Norrath has ever seen--I do not waste my time on brutes like you!");
		}
		#:: Separate response for bards, who are always special
		elsif ($class eq 'Bard') {
			#:: Send a message that only the client can see, in yellow (15) text
			$client->Message(15, "With just one look, I can see that your songbook is lacking, $name.  Would you like me to [" . quest::saylink("scribe") . "] all of the known $class songs for you?");
		}
		#:: Separate response for casting classes
		elsif ($class eq 'Beastlord' || $class eq 'Cleric' || $class eq 'Druid' || $class eq 'Enchanter' || $class eq 'Magician' || $class eq 'Necromancer' || $class eq 'Paladin' || $class eq 'Ranger' || $class eq 'Shadowknight' || $class eq 'Shaman' || $class eq 'Wizard') {
			#:: Send a message that only the client can see, in yellow (15) text
			$client->Message(15, "With just one look, I can see that your spellbook is lacking, $name.  Would you like me to [" . quest::saylink("scribe") . "] all of the known $class spells for you?");
		}
	}
	#:: Match text for "scribe", case insensitive
	elsif ($text=~/scribe/i) {
		if ($class eq 'Bard' || $class eq 'Beastlord' || $class eq 'Cleric' || $class eq 'Druid' || $class eq 'Enchanter' || $class eq 'Magician' || $class eq 'Necromancer' || $class eq 'Paladin' || $class eq 'Ranger' || $class eq 'Shadowknight' || $class eq 'Shaman' || $class eq 'Wizard') {
			#:: Clear out any existing spells
			quest::unscribespells();
			#:: Scribe all spells up to the user's level
			quest::scribespells($ulevel, 0);
			#:: Send a message that only the client can see, in yellow (15) text
			$client->Message(15, "You look like a more powerful caster already! Go out and test your new spells!");
			#:: Play a Ding! sound
			quest::ding();
		}
		elsif ($class eq 'Berserker' || $class eq 'Monk' || $class eq 'Rogue' || $class eq 'Warrior') {
			$client->Message(15, "Begone, $class--lest I turn you into froglok tad!");
		}
	}
}

sub EVENT_ITEM {
	#:: Return unused items since we don't expect any handins
	plugin::returnUnusedItems();
}
```
As with disciplines, if you would prefer that your players do not have to interact with an NPC, it is quite simple to add all new spells/songs each time a player levels using a perl script:

* File Name: global/global_player.pl (add this code to the existing script file)
* Description:  This script will scribe all new spells/songs when a player levels up.

```perl
sub EVENT_LEVEL_UP {
	#:: Scribe all spells/songs, maximum set to player's level, minimum set to the level prior
	quest::scribespells($ulevel,$ulevel - 1);
}
```

# Skill Maxer (PERL)

* File Name (example): Scotty_the_Skilled.pl
* Description:  This script will set all available skills to maximum at the player's current level.

```perl
sub EVENT_SAY {
	#:: Match text for "hail", case insensitive
	if ($text=~/hail/i) {
		#:: Send a message that only the client can see, in yellow (15) text
		$client->Message(15, "Hello, $name!  It appears you could use some help with your [" . quest::saylink("skills") . "].  Would you like me to teach you?");
	}
	#:: Match text for "skills", case insensitive
	elsif ($text=~/skills/i) {
		#:: Set available (non-trade, non-casting specialization) skills to maximum for race/class at current level
		foreach my $skill ( 0 .. 42, 48 .. 54, 70 .. 74 ) {
			next unless $client->CanHaveSkill($skill);
			#:: Create a scalar variable to store each skill's maximum skill level at the player's current level
			my $maxSkill = $client->MaxSkill($skill, $client->GetClass(), $ulevel);
			#:: Check that the player's skill does not already exceed the maximum skill based on level
			next unless $maxSkill > $client->GetRawSkill($skill);
			#:: Set the skill to the maximum
			$client->SetSkill($skill, $maxSkill);
		}
		#:: Send a message that only the client can see, in yellow (15) text
		$client->Message(15, "You look like a more capable $class already! Go out and test your new skills!");
		#:: Play a Ding! sound
		quest::ding();
	}
}

sub EVENT_ITEM {
	#:: Return unused items since we don't expect any handins
	plugin::returnUnusedItems();
}
```

As with spells and disciplines, if you would prefer that your players do not have to interact with an NPC, it is quite simple to max all skills each time a player levels using a perl script:

* File Name: global/global_player.pl (add this code to the existing script file)
* Description:  This script will max all skills when a player levels up.

```perl
sub EVENT_LEVEL_UP {
	#:: Set available (non-trade, non-casting specialization) skills to maximum for race/class at current level
	foreach my $skill ( 0 .. 42, 48 .. 54, 70 .. 74 ) {
		next unless $client->CanHaveSkill($skill);
		#:: Create a scalar variable to store each skill's maximum skill level at the player's current level
		my $maxSkill = $client->MaxSkill($skill, $client->GetClass(), $ulevel);
		#:: Check that the player's skill does not already exceed the maximum skill based on level
		next unless $maxSkill > $client->GetRawSkill($skill);
		#:: Set the skill to the maximum
		$client->SetSkill($skill, $maxSkill);
	}
}
```
