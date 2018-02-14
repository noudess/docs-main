EVENT_NPC_SLAY is triggered when one NPC kills another NPC.  Obvious opportunities for use would include city guards slaying newbie mobs, vermin being exterminated, etc.  Many of these flavor text opportunities are already covered with by the default-actions plugin.  Note the difference with [Perl EVENT_SLAY](https://github.com/EQEmu/Server/wiki/Perl-EVENT_SLAY), which is used when an NPC kills a player.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
killed|int|
### Example
```perl
sub EVENT_NPC_SLAY {
	quest::say($killed); # returns int
}
```

### Triggered

* When an NPC kills another NPC

### Example

```perl
sub EVENT_NPC_SLAY {
     quest::say("Another unworthy opponent. Never cross Mining Guild 628!!");
 }
```

Generated On 2018-01-15T22:07:30-08:00