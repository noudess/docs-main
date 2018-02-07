EVENT_SLAY is triggered when an NPC kills a player.  Often this event is used for some flavor messages, or to spawn adds.  Do not confuse this event with [EVENT_DEATH_COMPLETE](https://github.com/EQEmu/Server/wiki/Perl-EVENT_DEATH_COMPLETE) or [EVENT_DEATH](https://github.com/EQEmu/Server/wiki/Perl-EVENT_DEATH), which are used when a player kills an NPC.

### Triggered

* When an NPC kills a player

### Example

* This is a well-known example from Emperor Ssraeshza, who mocks any player that he kills

```perl
sub EVENT_SLAY {
	quest::say("Your god has found you lacking.");
}
```