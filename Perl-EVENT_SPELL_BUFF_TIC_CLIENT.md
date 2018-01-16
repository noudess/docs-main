EVENT_SPELL_BUFF_TIC_CLIENT
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
caster_id|int|
### Example
```perl
sub EVENT_SPELL_BUFF_TIC_CLIENT {
	quest::say($caster_id); # returns int
}
```

Generated On 2018-01-15T22:07:30-08:00