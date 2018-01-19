EVENT_ENTER is triggered when a player moves into proximity of the NPC.  Proximity is defined by quest::set_proximity(min_x, max_x, min_y, max_y, min_z, max_z).  

See [quest::set_proximity](https://github.com/EQEmu/Server/wiki/Perl-Quest-set_proximity) for more information on setting a proximity.

### Exports

### Triggered

* When a player moves into proximity of the NPC

### Examples

* This example establishes the NPC's proximity and checks to see if the player has an item before the NPC speaks.

```perl
sub EVENT_SPAWN {
     #:: Set the proximity bounds around the NPC on spawn, 15 unit radius
     my $x;
     my $y;
     $x = $npc->GetX();
     $y = $npc->GetY();
     quest::set_proximity($x-15,$x+15,$y-15,$y+15);
}

sub EVENT_ENTER {
     #::: Check and see if the player who enters is carrying Item ID 17005 - Backpack
     if (plugin::check_hasitem($client, 17005)) {
          quest::say("Hey, nice backpack!");
     }
}
```