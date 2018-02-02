EVENT_SPAWN is triggered when an NPC spawns.  This event is often used to start timers, attack player targets, establish NPC HP events or proximities, start dialogues, and more.  

### Triggered

* When the NPC spawns.

### Examples

* This example establishes the NPC's proximity under the spawn event, and speaks a message once the player has entered and then exits that proximity using [EVENT_EXIT](https://github.com/EQEmu/Server/wiki/Perl-EVENT_EXIT)

```perl
sub EVENT_SPAWN {
     #:: Set the proximity bounds around the NPC on spawn, 15 unit radius
     my $x;
     my $y;
     $x = $npc->GetX();
     $y = $npc->GetY();
     quest::set_proximity($x-15,$x+15,$y-15,$y+15);
}

sub EVENT_EXIT {
     #:: Triggered when the player leaves the NPC's proximity
     quest::say("Come back soon!");
}
```

* In this example, the NPC would depop when its health reaches 50 percent as set by [quest::setnexthpevent()](https://github.com/EQEmu/Server/wiki/Perl-Quest-setnexthpevent)

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

* You can also use this event to set special attacks, run states, sit states, etc.
* In this example, the NPC will immediately run and attack a nearby player while shouting its war cry

```perl
sub EVENT_SPAWN {
     #:: Set the NPC to run
     quest::SetRunning(1);
     #:: Shout out a war cray
     quest::shout("For Jotenheimr!!!");
     #:: Try to find a random client within 200 units of the NPC
     my $rClient = $entity_list->GetRandomClient($x,$y,$z, 200);
     #:: If there's a random sucker nearby, attack them
     if ($rClient) {
          quest::attack($rClient->GetName());
     }
}
```