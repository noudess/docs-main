EVENT_PROXIMITY_SAY is triggered when a player uses say within proximity of the NPC, without needing to target the NPC.  Proximity is defined by quest::set_proximity(min_x, max_x, min_y, max_y, min_z, max_z).  Don't forget to enable proximity say using the quest::enable_proximity_say() function.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
data|int|
text|int|
langid|int|
### Example
```perl
sub EVENT_PROXIMITY_SAY {
	quest::say($data); # returns int
	quest::say($text); # returns int
	quest::say($langid); # returns int
}
```

### Triggered

* When a player uses say near an NPC with a defined proximity and proximity say enabled.
* It is not necessary to have the NPC targeted.  

### Example

* In this example, if a player near the NPC says "hello?", the NPC will respond

```perl
sub EVENT_SPAWN {
     #:: Set the proximity bounds around the NPC on spawn, 15 unit radius
     my $x;
     my $y;
     $x = $npc->GetX();
     $y = $npc->GetY();
     quest::set_proximity($x-15,$x+15,$y-15,$y+15);
     #:: Enable the NPC to listen for say messages within the proximity
     quest::enable_proximity_say();
}

sub EVENT_PROXIMITY_SAY {
     #:: Match the say message like "hello", the "i" is for case-insensitive.
     if ($text=~/hello/i) {
          quest::say("Get over here and talk to me, $name!");
     }
}
```

Generated On 2018-01-15T22:07:30-08:00