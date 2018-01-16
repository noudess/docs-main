EVENT_GROUP_CHANGE
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
grouped|int|
raided|int|
### Example
```perl
sub EVENT_GROUP_CHANGE {
	quest::say($grouped); # returns int
	quest::say($raided); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00