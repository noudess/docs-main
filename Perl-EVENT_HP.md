EVENT_HP is triggered when an NPC's hit points reach the percent specified by [quest::setnexthpevent()](https://github.com/EQEmu/Server/wiki/Perl-Quest-setnexthpevent).  This event is often used for dialogue, spawning adds, or depopping the NPC.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
hpevent|int|
inchpevent|int|
hpevent|int|
inchpevent|int|
### Example
```perl
sub EVENT_HP {
	quest::say($hpevent); # returns int
	quest::say($inchpevent); # returns int
	quest::say($hpevent); # returns int
	quest::say($inchpevent); # returns int
}
```

### Triggered

* When an NPC's health reaches the specified percentage.

### Examples

* In this example, the NPC would depop when its health reaches 50 percent.

```perl
sub EVENT_SPAWN {
     #:: Set the threshold (by percent) to trigger the HP Event - 50 percent
     quest::setnexthpevent(50);
}

sub EVENT_HP {	
     #:: Once the NPC's health reaches the percentage specified, depop
     if ($hpevent == 50) {
          quest::depop();
     }
}
```

* In this example, we will spawn adds at our first HP event trigger, and set the threshold for the next HP event
* At the second HP event trigger, we will spawn more adds

```perl
sub EVENT_SPAWN {
     #:: Set the threshold (by percent) to trigger the first HP Event - 50 percent
     quest::setnexthpevent(50);
}

sub EVENT_HP {
     #:: Use numeric comparison to match the percentage specified - 50 percent
     if ($hpevent == 50) {
          #:: Spawn two A_Mangled_Vegerog adds at the NPC's current location
          quest::spawn2(218023,0,0,$x,$y,$z,$h);
          quest::spawn2(218023,0,0,$x,$y,$z,$h);
          #:: Set the threshold (by percent) to trigger the next HP Event - 15 percent
          quest::setnexthpevent(15);
     }
     #:: Use numeric comparison to match the percentage specified - 15 percent
     if ($hpevent == 15) {
          #:: Spawn four A_Mangled_Vegerog adds at the NPC's current location
          quest::spawn2(218023,0,0,$x,$y,$z,$h);
          quest::spawn2(218023,0,0,$x,$y,$z,$h);
          quest::spawn2(218023,0,0,$x,$y,$z,$h);	
          quest::spawn2(218023,0,0,$x,$y,$z,$h);				
     }
}
```

Generated On 2018-01-15T22:07:30-08:00