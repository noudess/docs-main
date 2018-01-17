When an NPC receives a signal from [[quest::signal()|Perl-Quest-signal]], [[quest::signalwith()|Perl-Quest-signalwith]], or [[quest::crosszonesignalnpcbynpctypeid()|Perl-Quest-crosszonesignalnpcbynpctypeid]], it run cause this event to trigger. Using this event is not recommended for more complicated scripts, look into <link?> encounter system instead.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
signal|int|
### Example
```perl
sub EVENT_SIGNAL {
	quest::say($signal); # returns int
}
```

### Triggered

* Triggered using quest::signal(NPC_ID,wait_time) or quest::signalwith(NPC_ID,signal_ID,wait_time).
* Generally a way to have one NPC cause another NPC to do something.
* Often used with "controller" NPCs that coordinate events.

### Example

* This example would have the NPC depop if it receives a signal with ID "17":

```perl
sub EVENT_SIGNAL {
     #::: Please add a note about where this signal originates (IE "sent from Other_NPC.pl")
     if ($signal == 17) {
          quest::depop();
     }
}
```

* This example increments a counter each time a signal with the appropriate ID is received.

```perl
my $count = 0;

sub EVENT_SIGNAL {
     #::: Signal 1 is from the clockwork spiders being killed.
     if ($signal == 1) {
          $count++;
          if ($count == 1) {
               #::: Start a three minute timer to spawn targetable Manaetic Behemoth
               quest::settimer("wake", 180);
          }
     }
     #::: Signal 2 is from the clockwork spiders reaching Manaetic Behemoth.
     if ($signal == 2) {
          #::: Reset the count and make them start over.
          $count = 0;
          quest::stoptimer("wake");
     }
}

sub EVENT_TIMER {
     #::: This uses eq for a string comparison to match the timer "wake".
     #::: Check the count to make sure the clockwork spiders were killed and not just kited. 
     if ($timer eq "wake" && $count >= 12) {
          quest::stoptimer("wake");
          #::: Spawn the targetable version of Manaetic Behemoth in place
          quest::spawn2(206074,0,0,$x,$y,$z,0);
          #::: Depop the untargetable version of Manaetic Behemoth with respawn timer active.
          quest::depop_withtimer();
     }
}
```

Generated On 2018-01-15T22:07:30-08:00