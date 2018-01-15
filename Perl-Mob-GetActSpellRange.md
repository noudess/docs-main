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