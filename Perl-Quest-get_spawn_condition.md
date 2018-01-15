gets a quest  spawn condition.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
zone_short|string|
instance_id|int|
condition_id|int|

### Example

```perl
my $zone_short = "test";
my $instance_id = 1;
my $condition_id = 1;
my $val = quest::($zone_short, $instance_id, $condition_id);
quest::say($val); # Returns uint
```