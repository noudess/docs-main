
EVENT_WAYPOINT_ARRIVE
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
wp|int|
### Example
```perl
sub EVENT_WAYPOINT_ARRIVE {
	quest::say($wp); # returns int
}
```

### Triggered

* When an NPC reaches a grid waypoint entry

### Example

* This example would cause your NPC to speak once it reaches a particular waypoint. 
* Don't forget to count waypoint 0 (the spawn point)

```perl
sub EVENT_WAYPOINT_ARRIVE {
     #::: When NPC arrives at waypoint 11
     if ($wp == 11) {
          quest::say("Wow, that was a long walk!");
     }
}
```

Generated On 2018-01-15T22:07:30-08:00