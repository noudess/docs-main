CalculateHeadingToTarget.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
in_x||
in_y||

### Example

```perl
my $in_x = 1;
my $in_y = 1;
my $val = $mob->CalculateHeadingToTarget($in_x, $in_y);
quest::say($val); # Returns int
```