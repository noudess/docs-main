is a mob immune to spell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
caster||

### Example

```perl
my $spell_id = 1;
my $caster = 1;
my $val = $mob->IsImmuneToSpell($spell_id, $caster);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00