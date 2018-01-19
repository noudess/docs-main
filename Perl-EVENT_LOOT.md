EVENT_LOOT is used to check if a player has successfully looted an item or items.  Typically you would use this function in the zone player.pl or global_player.pl script files (not the script for the NPC).

It is probably more desirable to use the Task System and Activities so that item IDs and counts are stored in the database, and you don't have a global file full of loot events.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
looted_id|int|
looted_charges|int|
corpse|int|
### Example
```perl
sub EVENT_LOOT {
	quest::say($looted_id); # returns int
	quest::say($looted_charges); # returns int
	quest::say($corpse); # returns int
}
```

### Triggered

* When a player successfully loots an item off a corpse.

### Examples

* This example uses the loot event to match a particular item and corpse.
* Note that we use the NPC's name (Fippy_Darkpaw) and not the numeric corpse ID (IE 249) or full corpse name (IE Fippy_Darkpaw`s_corpse249).

```perl
sub EVENT_LOOT {
	#::: Use == for numeric comparison to Item ID 60396 - Fippy's Paw
	#::: Use eq for string comparison to Fippy_Darkpaw's corpse
	if ($looted_id == 60396 && $corpse eq "Fippy_Darkpaw") {
		$client->Message(15, "The bloody stump of Fippy's paw--it's a lot smaller than you thought it would be.");
	}
}
```

Generated On 2018-01-15T22:07:30-08:00