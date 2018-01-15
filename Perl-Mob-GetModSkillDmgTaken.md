gets a mob mod skill dmg taken.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
skill_num||

### Example

```perl
my $skill_num = 1;
my $val = $mob->GetModSkillDmgTaken($skill_num);
quest::say($val); # Returns int
```