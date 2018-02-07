EVENT_ATTACK is triggered when the NPC is attacked.  Often this event is used for flavor text or to spawn adds.  Do not confuse this event with [EVENT_AGGRO](https://github.com/EQEmu/Server/wiki/Perl-EVENT_AGGRO), which is triggered when the NPC aggros a player.

### Triggered

* When the NPC is attacked by a player

### Example

* This is a well-known example where Derakor the Vindicator (Vindi) shouts when attacked by a player

```perl
sub EVENT_ATTACK {
     quest::shout("Your kind will not defile the temple of Rallos Zek!");
}
```