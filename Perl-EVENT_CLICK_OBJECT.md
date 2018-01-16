EVENT_CLICK_OBJECT
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
objectid|int|
clicker_id|int|
### Example
```perl
sub EVENT_CLICK_OBJECT {
	quest::say($objectid); # returns int
	quest::say($clicker_id); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00