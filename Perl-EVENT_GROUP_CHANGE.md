EVENT_GROUP_CHANGE
### Arguments
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

Generated On 2018-01-15T22:01:49-08:00