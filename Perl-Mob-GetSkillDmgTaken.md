gets a mob skill dmg taken.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
skill_num||

### Example

```perl
my $skill_num = 1;
my $val = $mob->GetSkillDmgTaken($skill_num);
quest::say($val); # Returns uint
```