EVENT_FORAGE_SUCCESS
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
foraged_item|int|
### Example
```perl
sub EVENT_FORAGE_SUCCESS {
	quest::say($foraged_item); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00