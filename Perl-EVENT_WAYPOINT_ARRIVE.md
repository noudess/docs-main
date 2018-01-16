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

### Functionality Explained

EVENT_WAYPOINT_ARRIVE is triggered when an NPC reaches a grid waypoint entry.

### EVENT_WAYPOINT_ARRIVE in use

```perl
# This example would cause your NPC to speak once it reaches a particular waypoint. 
# Don't forget to count waypoint 0 (the spawn point)

sub EVENT_WAYPOINT_ARRIVE {

     # Use == for numeric comparison to match grid waypoint entry "11" 
     if ($wp == 11) {
          quest::say("Wow, that was a long walk!");
     }
}
```

Generated On 2018-01-15T22:07:30-08:00