ModifyNPCStat.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
stat_id|int|
str_value|string|

### Example

```perl
my $stat_id = 1;
my $str_value = "test";

quest::($stat_id, $str_value); # Returns void
```