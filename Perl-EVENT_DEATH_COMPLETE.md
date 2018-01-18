EVENT_DEATH_COMPLETE is triggered when an NPC is killed.  This event is often used to signal another mob, stop any timers, or spawn other NPCs.  

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
killer_id|int|
killer_damage|int|
killer_spell|int|
killer_skill|int|
### Example
```perl
sub EVENT_DEATH_COMPLETE {
	quest::say($killer_id); # returns int
	quest::say($killer_damage); # returns int
	quest::say($killer_spell); # returns int
	quest::say($killer_skill); # returns int
}
```

### Triggered

* This event is triggered when the NPC dies.

### Examples

* In this example, when the NPC dies, it sends a signal to another NPC. 

```perl
sub EVENT_DEATH_COMPLETE {
	#::: Wait 0 seconds and send a signal "1" to npc_type_id 206046 - Manaetic Behemoth
	quest::signalwith(206046,1,0);
}
```

* In this example, when the NPC dies, it spawns A Planar Projection at its current location.

```perl
sub EVENT_DEATH_COMPLETE {
     #::: Spawn npc_type_id 218068 - A_Planar_Projection on grid 0, guildwarset 0, at the NPC's X, Y, Z, and Heading
     quest::spawn2(218068,0,0,$x,$y,$z,$h);	
}
```
Generated On 2018-01-15T22:07:30-08:00