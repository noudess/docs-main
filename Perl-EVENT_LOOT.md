EVENT_LOOT
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

Generated On 2018-01-15T22:07:30-08:00