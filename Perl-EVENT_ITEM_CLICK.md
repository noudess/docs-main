EVENT_ITEM_CLICK
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
itemid|int|
itemname|int|
slotid|int|
spell_id|int|
### Example
```perl
sub EVENT_ITEM_CLICK {
	quest::say($itemid); # returns int
	quest::say($itemname); # returns int
	quest::say($slotid); # returns int
	quest::say($spell_id); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00