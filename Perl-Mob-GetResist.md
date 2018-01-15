gets a mob resist.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|

### Example

```perl
my $type = 1;
my $val = $mob->GetResist($type);
quest::say($val); # Returns int
```