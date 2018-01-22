EVENT_DEATH
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
client|client|client who killed mob
npc|npc|npc that was killed
killer_id|int|client ID of killer. (Does not seem castable to mob)
killer_damage|int|How much damage was dealt on killing blow
killer_spell|int|Spell ID used to kill mob
killer_skill|int|Skill ID used to kill mob
charid|int|Character ID who killed mob
class|string|Class Name who killed mob
faction|int|Faction comparison of killed mob vs killer
h|float|heading of mob during death
hpratio|float|percent health of mob after death (negative value)
mlevel|int|level of mob killed
mname|string|name of mob killed
mobid|int|id of mob killed
name|string|name of killer
race|string|race of killer
status|int|account status of killer
uguild_id|int|uguild of killer|
ulevel|int|level of killer
userid|int|user id of killer
x|float|x position of killed mob
y|float|y position of killed mob
z|float|z position of killed mob
zonehour|int|hour of zone when mob died
zoneid|int|zone id where mob died
zoneln|string|long name of zone where mob died
zonemin|int|minimum level to enter zone where mob died
zonesn|string|short name of zone where mob died
zonetime|int|time of zone where mob died
zoneweather|int|weather of zone where mob died
### Example
```perl
sub EVENT_DEATH {
	quest::say($killer_id); # returns int
	quest::say($killer_damage); # returns int
	quest::say($killer_spell); # returns int
	quest::say($killer_skill); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00