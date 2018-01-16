EVENT_FORAGE_SUCCESS
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
foraged_item|int|
### Example
```perl
sub EVENT_FORAGE_SUCCESS {
	quest::say($foraged_item); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00