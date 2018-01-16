EVENT_CAST_BEGIN
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
spell_id|int|
### Example
```perl
sub EVENT_CAST_BEGIN {
	quest::say($spell_id); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00