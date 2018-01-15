gets a mob act spell damage.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
value|int|

### Example

```perl
my $spell_id = 1;
my $value = 1;
my $val = $mob->GetActSpellDamage($spell_id, $value);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00