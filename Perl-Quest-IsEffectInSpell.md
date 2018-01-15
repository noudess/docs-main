is a quest effect in spell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
effect_id|int|

### Example

```perl
my $spell_id = 1;
my $effect_id = 1;
my $val = quest::IsEffectInSpell($spell_id, $effect_id);
quest::say($val); # Returns uint
```


Generated On 2018-01-15T13:04:48-08:00