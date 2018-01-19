EVENT_FISH_FAILURE is triggered when the player fishes without catching anything.  

Typically you would use this functionality in the zone player.pl or global_player.pl script files.

### Triggered

* When the player fails at fishing.

### Example

* This example displays an emote in gray when the player fails to catch anything after a fishing attempt.

```perl
sub EVENT_FISH_FAILURE {
     $client->Message(1, "Keep it down--you're scaring all the fish away!")
}
```