gets a mob skill.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
skill_num||

### Example

```perl
my $skill_num = 1;
my $val = $mob->GetSkill($skill_num);
quest::say($val); # Returns uint
```