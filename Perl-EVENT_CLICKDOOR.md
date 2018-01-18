EVENT_CLICKDOOR is triggered when a player clicks on a door or object that is a door.  Often this is used to check for player character flags, zone flags, or to move a player to a particular instance of a zone.  Since [doors](https://github.com/EQEmu/Server/wiki/doors) have [open types](https://github.com/EQEmu/Server/wiki/Door-Open-Types) and destination fields stored in the database, most "simple" doors do not require a separate quest script.

An example of a "simple" door would be any door that requires a single keyitem (by Item ID) to open, like the door to the basement in Befallen.  An example of a more complex door, would be any door that requires character flags, like the entrance to Crypt of Decay.  

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
doorid|int|
version|int|
### Example
```perl
sub EVENT_CLICKDOOR {
	quest::say($doorid); # returns int
	quest::say($version); # returns int
}
```

### Triggered

* When a client clicks on a door or door object.

### Example

* This example uses a [Quest Global](https://github.com/EQEmu/Server/wiki/quest_globals) to check if the player is able to open the door

```perl
sub EVENT_CLICKDOOR {
     #::: Use == for numeric comparison to match door_id 7 - the door to the Factory in the Plane of Innovation
     if ($doorid == 7) {
          #::: Check to see if the player has a Quest Global used to grant access to the door
          if (defined $qglobals{pop_poi_dragon}) {
               $client->Message(15,"You remember Nitram's words - 'three small turns to the right on the bottommost rivet should open the door'.");
               #::: Open the door by door_id
               quest::forcedooropen(7);
          }
     }
}
```

* This example uses Quest Globals or a level check to check if the player is able to open the door.
* This example would allow a user to pass a PoP door based on level, or progression flags, or alternate access flags.
* Since the door object requires a [zone_flag](https://github.com/EQEmu/Server/wiki/zone_flags), the flag is checked and set if not present.

```perl
$level_for_tier_two = 55;

sub EVENT_CLICKDOOR {
     #::: Use == for numeric comparison to match door_id 12 - the door object that leads to Crypt of Decay
     if ($doorid == 12) {
          #::: Use >= for numeric comparison to match if the player's level exceeds the minimum, set above
          #::: OR check to see if the player has a Quest Global used to grant access to the door
          if ($client->GetLevel() >= $level_for_tier_two || (defined $qglobals{pop_pod_alder_fuirstel} && defined $qglobals{pop_pod_grimmus_planar_projection} && defined $qglobals{pop_pod_elder_fuirstel}) || (defined $qglobals{pop_alt_access_codecay})) {
               #::: Check to see if the player has the zone_flags by zoneidnumber
               if (quest::has_zone_flag(200) != 1) {
                    #::: If the player did not have the zone_flags, set it by zoneidnumber
                    quest::set_zone_flag(200);
               }
          }
     }
}
```
Generated On 2018-01-15T22:07:30-08:00