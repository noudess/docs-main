EVENT_EXIT is triggered when a player leaves the proximity of the NPC.  Proximity is defined by quest::set_proximity(min_x, max_x, min_y, max_y, min_z, max_z).  

See [quest::set_proximity](https://github.com/EQEmu/Server/wiki/Perl-Quest-set_proximity) for more information on setting a proximity.

### Exports

### Triggered

* When a player moves out of the proximity of the NPC

### Examples

* This example establishes the NPC's proximity and speaks a message once the player has entered and then exits that proximity.

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
          quest::say("Come back soon!");
}
```