CanMobLoot.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
charid||

### Example

```perl
my $charid = 1;
my $val = $corpse->CanMobLoot($charid);
quest::say($val); # Returns bool
```