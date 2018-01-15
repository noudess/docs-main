gets a mob buff slot from type.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|

### Example

```perl
my $type = 1;
my $val = $mob->GetBuffSlotFromType($type);
quest::say($val); # Returns int
```