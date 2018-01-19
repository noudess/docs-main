EVENT_FISH_START is triggered when the player begins to fish.  

Typically you would use this functionality in the zone player.pl or global_player.pl script files.

### Triggered

* When the player begins to fish.

### Example

* This example displays an emote in gray when the player casts their line

```perl
sub EVENT_FISH_START {
	$client->Message(1, "You crack a beer and toss your line in.");
}
```