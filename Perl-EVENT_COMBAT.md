EVENT_COMBAT is triggered each time an NPC enters or leaves combat.  Note the difference between this event and [Perl EVENT_ATTACK](https://github.com/EQEmu/Server/wiki/Perl-EVENT_ATTACK), which is triggered when a player attacks an NPC, and [Perl EVENT_AGGRO](https://github.com/EQEmu/Server/wiki/Perl-EVENT_AGGRO), which is triggered when an NPC aggros a player.

This event is often used to start or stop timers (for timed events or to stop a despawn, for instance), send signals to controller NPCs, or simply add some flavor messages. 

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
combat_state|int|
### Example
```perl
sub EVENT_COMBAT {
	quest::say($combat_state); # returns int
}
```

### Triggered

* When the combat state of an NPC changes

### Examples

* In this example, we add flavor text to the NPC when combat is entered by matching the $combat_state
* This could easily be scripted using Perl EVENT_AGGRO as well

```perl
sub EVENT_COMBAT {
     #:: Match combat_state 1 (true) for entered combat
     if ($combat_state == 1) {
          quest::say("Time to die $name");
     }
}
```

* In this example, we stop a depop timer when the NPC enters combat within 30 minutes of spawning
* If the NPC isn't engaged within 30 minutes by the player, it will depop
* This is a simple example and doesn't script what happens if the player dies and the NPC's combat state returns to 0

```perl
sub EVENT_SPAWN {
     #:: Start a timer that is named "depop", the duration is 1,800 seconds (30 minutes)
     quest::settimer("depop",1800); 
}

sub EVENT_TIMER {
     #:: Use eq for string comparison to match timer "depop"
     if ($timer eq "depop") {
          #:: Stop timer "depop" from looping
          quest::stoptimer("depop");
          quest::depop();
     }
}

sub EVENT_COMBAT {
     #:: Match combat_state 1 (true) for entered combat
     if ($combat_state == 1) {
          quest::stoptimer("depop");
     }
}
```


Generated On 2018-01-15T22:07:30-08:00