EVENT_PLAYER_PICKUP is triggered when a PC picks up an item (like a ground spawn, for instance).  

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
picked_up_id|int|
picked_up_entity_id|int|
### Example
```perl
sub EVENT_PLAYER_PICKUP {
	quest::say($picked_up_id); # returns int
	quest::say($picked_up_entity_id); # returns int
}
```

### Triggered

* When a client picks up an item from the ground.

### Example

* This example will display a message to the client when a particular item is picked up off the ground.

```perl
sub EVENT_PLAYER_PICKUP {
     #::: Use == for numeric comparison to Item ID 5551 - Bluetoe Mushroom
     if ($picked_up_id == 5551) {
          $client->Message(15, "Yay, you found a Bluetoe Mushroom!");
     }
}
```


Generated On 2018-01-15T22:07:30-08:00