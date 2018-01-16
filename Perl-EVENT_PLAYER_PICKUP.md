EVENT_PLAYER_PICKUP
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

Generated On 2018-01-15T22:07:30-08:00