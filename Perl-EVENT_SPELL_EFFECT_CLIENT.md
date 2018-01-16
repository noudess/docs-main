EVENT_SPELL_EFFECT_CLIENT
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
caster_id|int|
### Example
```perl
sub EVENT_SPELL_EFFECT_CLIENT {
	quest::say($caster_id); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00