EVENT_TIMER
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
timer|int|
### Example
```perl
sub EVENT_TIMER {
	quest::say($timer); # returns int
}
```

### Functionality Explained

EVENT_TIMER is triggered by a quest::settimer(timer_name,duration_in_seconds) or quest::settimerMS(timer_name,duration_in_milliseconds)

The timer will loop until it is stopped, and EVENT_TIMER will trigger each time that the duration of the timer elapses

Timers can be stopped using the quest::stopalltimers() or quest::stoptimer(timer_name) functions

### EVENT_TIMER in use

```perl
# this is an example of using a timer with a numeric name to cause an NPC to depop 30 minutes after it spawns

sub EVENT_SPAWN { # when the NPC spawns

     quest::settimer(1,1800); # the name of the timer is "1", the duration is 1,800 seconds (30 minutes)
}

sub EVENT_TIMER { # when the duration elapses and the timer triggers

     if ($timer == 1) { # using == for numeric comparison to match timer "1"
          quest::stoptimer(1); # stop timer "1" from looping
          quest::depop(); # this would depop the NPC
     }
}
```

```perl
# this is an example of using a timer with a text string name to cause an NPC to depop 30 minutes after it spawns

sub EVENT_SPAWN { # when the NPC spawns

     quest::settimer("depop",1800); # the name of the timer is "depop", the duration is 1,800 seconds (30 minutes)
}

sub EVENT_TIMER { # when the duration elapses and the timer triggers

     if ($timer eq "depop") { # using eq for string comparison to match timer "depop"
          quest::stoptimer("depop"); # stop timer "depop" from looping
          quest::depop(); # this would depop the NPC
     }
}
```


```perl
# this is an example of using a timer with a numeric name to depop an NPC if it is not engaged in combat within two minutes of spawning

sub EVENT_SPAWN { # when the NPC spawns

     quest::settimer(4,120); # the name of the timer is "4", the duration is 120 seconds (2 minutes)
}
	
sub EVENT_COMBAT { # when the NPC is engaged in combat

     quest::stoptimer(4); # stop timer "4" from looping
}
	
sub EVENT_TIMER { # when the duration elapses and the timer triggers

     if ($timer == 4) { # using == for numeric comparison to match timer "4"
          quest::stoptimer(4); # stop timer "4" from looping
          quest::depop_withtimer(); # depop using the normal spawn timer
     }
}
```


```perl
# this is an example of using two timers with numeric names, started by separate events
# the NPC will depop two hours after it spawns
# the NPC will shout to taunt attackers once it has been engaged

sub EVENT_SPAWN { # when the NPC spawns

     quest::settimer(1,7200); # the name of the timer is "1", the duration is 7,200 seconds (2 hours)
}

sub EVENT_AGGRO { # when the NPC is aggro'd

     quest::settimer(2,60); # the name of the timer is "2", the duration is 60 seconds (1 minute)
}

sub EVENT_TIMER { # when the duration elapses and the timer triggers

     if ($timer == 1) { # using == for numeric comparison to match timer "1"
          quest::stoptimer(1); # stop the timer "1" from looping
          quest::stoptimer(2); # stop the timer "2" from looping
          quest::depop(); # this would depop the NPC
     }

     if ($timer == 2) { # using == for numeric comparison to match timer "2"
          if ($npc->IsEngaged()) { # check to see if the NPC is engaged
               quest::shout("You will never defeat me!!!"); # shout so that the whole zone hears you
          }
     }
}

sub EVENT_DEATH_COMPLETE { # when the NPC is killed

     quest::say("You have defeated me..."); # not so shouty now
     quest::stoptimer(1); # stop the timer "1" from looping
     quest::stoptimer(2); # stop the timer "2" from looping
}
```

Generated On 2018-01-15T22:07:30-08:00