
EVENT_WAYPOINT_DEPART
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
wp|int|
### Example
```perl
sub EVENT_WAYPOINT_DEPART {
	quest::say($wp); # returns int
}
```

### Triggered

* When an NPC leaves its current grid waypoint entry

### Example

* This example would cause your NPC to speak as it departs a particular waypoint. 
* Don't forget to count waypoint 0 (the spawn point) when using waypoint events.

```perl
sub EVENT_WAYPOINT_DEPART {
     # If we departed waypoint 0
     if ($wp == 0) {
          quest::say("And we're off!");
     }
}
```
Generated On 2018-01-15T22:07:30-08:00