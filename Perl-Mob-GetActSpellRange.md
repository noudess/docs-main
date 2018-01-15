gets a mob act spell range.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
range||

### Example

```perl
my $spell_id = 1;
my $range = 1;
my $val = $mob->GetActSpellRange($spell_id, $range);
quest::say($val); # Returns double
```


Generated On 2018-01-15T13:04:48-08:00