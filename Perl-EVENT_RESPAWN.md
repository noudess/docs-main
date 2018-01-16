EVENT_RESPAWN
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
option|int|
resurrect|int|
### Example
```perl
sub EVENT_RESPAWN {
	quest::say($option); # returns int
	quest::say($resurrect); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00