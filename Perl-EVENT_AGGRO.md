EVENT_AGGRO is triggered when an NPC aggros a player.  This event is often used to start timers (for timed events), send signals to controller NPCs, or simply add some flavor messages.  Do not confuse this event with [EVENT_ATTACK](https://github.com/EQEmu/Server/wiki/Perl-EVENT_ATTACK), which is triggered when an NPC is attacked.  An example of this differentiation would be a guard attacking a player due to poor faction, vs. a player hitting the guard.

### Triggered

* When an NPC aggros a player

### Example

* In this example, the City Guard will speak a random message as he happily attacks some poor newb.

```perl
sub EVENT_AGGRO {
     #:: Set a 'random' scalar value to choose which message to speak
     my $random = int(rand(3));
     #:: Use == for numeric comparison to the 'random' message of choice
     if($random == 0) {
          quest::say("$class like you are an affront to my senses!");
     }
     if($random == 1) {
          quest::say("$class like you always bring out the worst in me!");
     }
     if($random == 2) {
          quest::say("It's $class like you that insult all of Norrath!");
     }
}
```