gets a raid total raid damage.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
other||

### Example

```perl
my $other = 1;
my $val = $raid->GetTotalRaidDamage($other);
quest::say($val); # Returns uint
```