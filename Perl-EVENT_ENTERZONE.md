EVENT_ENTERZONE is triggered when a player enters a zone--not to be confused with [Perl EVENT_ZONE](https://github.com/EQEmu/Server/wiki/Perl-EVENT_ZONE), which is triggered when a player LEAVES a zone.  

This event allows you to send the player an emote (like the Wayfarer Brotherhood text), set a compass mark (for an LDON adventure), start timers, check tasks, and a great number of other functions.  

This perl event is most commonly used in the zone's player.pl file, or in the global_player.pl file.

### Triggered

* When a player enters a zone.

### Examples

* In this example, every time someone enters the zone, they will hear the DING! sound that plays when you gain a level.

```perl
sub EVENT_ENTERZONE {
     #:: Because it's funny.
     quest::ding();
}
```

* In this example, when a player is part of a Rujarkian Hills Adventure, they will see a mark on their compass. 

```perl
sub EVENT_ENTERZONE {
     #:: Create a scalar for storing the instance ID
     $RujDInstance = quest::GetInstanceID("rujd",50);
     #:: If the instance ID exists, it should be greater than 0--mark the player's compass if it is
     if ($RujDInstance > 0) {
          #:: Create a line on the compass leading the player to X,Y,Z
          $client->MarkCompassLoc(-157.09, 19.31, 100);
     }
}
```

* In this example, we set the player's 1H Slashing skill (Skill ID 1) to zero if we haven't set it to zero before.
* We then set a quest global so that we don't zero the skill out the next time the player enters a zone.

```perl
sub EVENT_ENTERZONE {
     #:: Check that the 'onehandslashingzerodout' quest global does not exist
     if (!defined $qglobals{"onehandslashingzerodout"}) {
          #:: Set the skill ID 1 to value 0
          $client->SetSkill(1, 0);
          #:: Set a quest global so that we do not zero the skill on the next zone in
          quest::setglobal("onehandslashingzerodout", 1, 5, "F");
     }
}
```