gets a mob caster level.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|

### Example

```perl
my $spell_id = 1;
my $val = $mob->GetCasterLevel($spell_id);
quest::say($val); # Returns int
```