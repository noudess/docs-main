EVENT_COMBAT
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
combat_state|int|
### Example
```perl
sub EVENT_COMBAT {
	quest::say($combat_state); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00