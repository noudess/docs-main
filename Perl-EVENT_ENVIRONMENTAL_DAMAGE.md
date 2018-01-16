EVENT_ENVIRONMENTAL_DAMAGE
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
env_damage|int|
env_damage_type|int|
env_final_damage|int|
### Example
```perl
sub EVENT_ENVIRONMENTAL_DAMAGE {
	quest::say($env_damage); # returns int
	quest::say($env_damage_type); # returns int
	quest::say($env_final_damage); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00