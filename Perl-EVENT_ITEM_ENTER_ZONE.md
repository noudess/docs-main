EVENT_ITEM_ENTER_ZONE
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
itemid|int|
itemname|int|
### Example
```perl
sub EVENT_ITEM_ENTER_ZONE {
	quest::say($itemid); # returns int
	quest::say($itemname); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00