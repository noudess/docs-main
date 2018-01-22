EVENT_SAY
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
client|client|Client who did say event
npc|npc|Npc who is handling say event
charid|int|character id of who did say event
class|string|class of who did say event
data|int|unknown? 124078
faction|int|faction comparison of who did say and npc
h|float|heading position of npc
hpratio|float|hp ratio e.g. 100
instanceid|int|instance id of zone, typically 0
instanceversion|int|instance version of zone, typically 0
langid|int|language id, common is 0
mlevel|int|mob level of npc
mname|string|mob name of npc
mobid|int|mob entity id of npc
name|string|name of who did say event
race|string|race of who did say event
status|int|account status of who did say event
text|string|Text of who did say event
uguild_id|int|guild id of who did say event
uguildrank|int|guild rank of who did say event
ulevel|int|level of who did say event
userid|int|user id of who did say event
x|float|x position of npc
y|float|y position of npc
z|float|z position of npc
zonehour|int|hour of zone when mob died
zoneid|int|zone id where mob died
zoneln|string|long name of zone where mob died
zonemin|int|minimum level to enter zone where mob died
zonesn|string|short name of zone where mob died
zonetime|int|time of zone where mob died
zoneweather|int|weather of zone where mob died
### Example
```perl
sub EVENT_SAY {
	quest::say($data); # returns int
	quest::say($text); # returns int
	quest::say($langid); # returns int
}
```

### Triggered

* When a PC targets and speaks to an NPC.

### Examples

* This example is a response to a "hail"

```perl
sub EVENT_SAY {
     #::: Checks if the text is like "Hail", the "i" is for case-insensitive.
     if ($text=~/Hail/i) {
          quest::say("Hello, $name!");
     }
}
```

* This example additionally checks the language of the "hail", and will only respond to text in that language.

```perl
sub EVENT_SAY {
     #::: Checks to see if the language is Thieves Cant (language ID 10)
     if ($langid == 10) {
          #::: Checks if the text is like "Hail", the "i" is for case-insensitive.
          if ($text=~/Hail/i) {
               # Respond, using the same language
               quest::say("Hello, $name!",10);
          }
     }
}
```


Generated On 2018-01-15T22:07:30-08:00