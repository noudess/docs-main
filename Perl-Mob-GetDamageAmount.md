gets a mob damage amount.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
tmob||

### Example

```perl
my $tmob = 1;
my $val = $mob->GetDamageAmount($tmob);
quest::say($val); # Returns uint
```