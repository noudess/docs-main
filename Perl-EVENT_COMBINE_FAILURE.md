EVENT_COMBINE_FAILURE is triggered when a player fails to make a trade skill combine. You would typically use this event in your zone player.pl (or global_player.pl) files.

Note that this event is in addition to the typical trade skill combine messages. You can use this event to add additional flavor, trigger other events, etc.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
recipe_id|int|
recipe_name|int|
### Example
```perl
sub EVENT_COMBINE_FAILURE {
	quest::say($recipe_id); # returns int
	quest::say($recipe_name); # returns int
}
```

### Triggered

* When a player fails to makes a trade skill combine

### Example

* In this example, we send the client a message when they fail to combine a Hand Made Backpack

```perl
sub EVENT_COMBINE_FAILURE {
     #:: Match Recipe 2686: "Hand Made Backpack" by ID
     if ($recipe_id == 2686) {
          #:: Send the client a message in color 15 (yellow)
          $client->Message(15,"Awww...now where are you going to put all of your stuff?");
     }
}
```

Generated On 2018-01-15T22:07:30-08:00