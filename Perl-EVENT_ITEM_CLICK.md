EVENT_ITEM_CLICK is triggered when a client clicks an item with a click effect.  This is a useful script to put in the Global quest scripts directory, so that you can make an item click work anywhere in the world.  

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

### Triggered 

* Triggered when a client clicks on item with a click effect.

### Examples

* This example is taken from the Evil Eye Costume Kit, which is part of the Halloween Costume illusion items.
* Note that the `scriptfileid` field for the item is set to 30073 in the database.
* Note that a corresponding quest file exists at global/items/script_30073.pl. 

```perl
sub EVENT_ITEM_CLICK {
     #::: Use == for numeric comparison to Item ID 54711 - Evil Eye Costume Kit
     if ($itemid == 54711) {
          #::: Change the player's race to 469 - Evil Eye
          quest::playerrace(469);
     } 
}
```

Generated On 2018-01-15T22:07:30-08:00