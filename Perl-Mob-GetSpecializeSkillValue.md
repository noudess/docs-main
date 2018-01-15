gets a mob specialize skill value.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|

### Example

```perl
my $spell_id = 1;
my $val = $mob->GetSpecializeSkillValue($spell_id);
quest::say($val); # Returns uint
```