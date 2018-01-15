gets a group total group damage.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
other||

### Example

```perl
my $other = 1;
my $val = $group->GetTotalGroupDamage($other);
quest::say($val); # Returns uint
```