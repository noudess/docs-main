EVENT_DROP_ITEM
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
quantity|int|
itemname|int|
itemid|int|
spell_id|int|
slotid|int|
### Example
```perl
sub EVENT_DROP_ITEM {
	quest::say($quantity); # returns int
	quest::say($itemname); # returns int
	quest::say($itemid); # returns int
	quest::say($spell_id); # returns int
	quest::say($slotid); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00