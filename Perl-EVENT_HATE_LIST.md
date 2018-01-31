EVENT_HATE_LIST is triggered each time a new player is added to, or leaves an NPC's hate list.  Note that this is not necessarily the same thing as being killed by the NPC (which might use [EVENT_SLAY](https://github.com/EQEmu/Server/wiki/Perl-EVENT_SLAY)); for instance, the player could camp out and be removed from the NPC's hate list.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
hate_state|int|
### Example
```perl
sub EVENT_HATE_LIST {
	quest::say($hate_state); # returns int
}
```

### Triggered

* When a player initially attacks an NPC or once a player leaves the NPC's hate list.

### Example

* This example uses the hate list to say a message

```perl
sub EVENT_HATE_LIST {
     #:: When the player appears the NPC's hate list
     if ($hate_state == 1) {
          quest::say("$name is gonna die!");
     }
     #:: When the player on the NPC's hate list leaves that hate list
     if ($hate_state == 0) {
          quest::say("$name is no match for my might!");
     }
}
```

Generated On 2018-01-15T22:07:30-08:00