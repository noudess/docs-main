EVENT_CLICK_DOOR
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
doorid|int|
version|int|
### Example
```perl
sub EVENT_CLICK_DOOR {
	quest::say($doorid); # returns int
	quest::say($version); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00