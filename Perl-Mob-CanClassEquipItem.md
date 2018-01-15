CanClassEquipItem.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
item_id|int|

### Example

```perl
my $item_id = 1;
my $val = $mob->CanClassEquipItem($item_id);
quest::say($val); # Returns bool
```