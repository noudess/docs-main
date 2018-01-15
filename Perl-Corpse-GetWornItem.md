gets a corpse worn item.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
equipSlot||

### Example

```perl
my $equipSlot = 1;
my $val = $corpse->GetWornItem($equipSlot);
quest::say($val); # Returns uint
```