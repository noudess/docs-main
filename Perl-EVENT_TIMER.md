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

### Triggered

* triggered by a quest::settimer(timer_name,duration_in_seconds) or quest::settimerMS(timer_name,duration_in_milliseconds)

* The timer will loop until it is stopped, and EVENT_TIMER will trigger each time that the duration of the timer elapses

* Timers can be stopped using the quest::stopalltimers() or quest::stoptimer(timer_name) functions

### Examples

* this is an example of using a timer with a string name to cause an NPC to depop 30 minutes after it spawns

```perl
sub EVENT_SPAWN {
     # Start a timer that is named "depop", the duration is 1,800 seconds (30 minutes)
     quest::settimer("depop",1800); 
}

sub EVENT_TIMER {
     # Use eq for string comparison to match timer "depop"
     if ($timer eq "depop") {
          # Stop timer "depop" from looping
          quest::stoptimer("depop"); 
          quest::depop(); 
     }
}
```

* This is an example of using two timers with numeric names, started by separate events
* The NPC will depop two hours after it spawns
* The NPC will shout every minute to taunt attackers once it has been engaged

```perl
sub EVENT_SPAWN { 
     # Start a timer that is named "depop", the duration is 7,200 seconds (2 hours)
     quest::settimer("depop",7200);
}

sub EVENT_AGGRO {
     # Start a timer that is named "engaged", the duration is 60 seconds (1 minute)
     quest::settimer("engaged",60);
}

sub EVENT_TIMER {
     # Use eq for string comparison to match timer "depop"
     if ($timer eq "depop") {
          # Stop the timer "depop" from looping
          quest::stoptimer("depop"); 
          # Stop the timer "engaged" from looping
          quest::stoptimer("engaged"); 
          quest::depop();
     }

     # Use eq for string comparison to match timer "engaged"
     if ($timer eq "engaged") {
          # Check to see if the NPC is engaged
          if ($npc->IsEngaged()) { 
               quest::shout("You will never defeat me!!!");
          }
     }
}

sub EVENT_DEATH_COMPLETE {
     quest::say("You have defeated me...");
     # Stop the timer "depop" from looping
     quest::stoptimer("depop");
     # Stop the timer "engaged" from looping
     quest::stoptimer("engaged");
}
```

Generated On 2018-01-15T22:07:30-08:00