CanHaveSkill.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
skill_id||

### Example

```perl
my $skill_id = 1;
my $val = $client->CanHaveSkill($skill_id);
quest::say($val); # Returns bool
```