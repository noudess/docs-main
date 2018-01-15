targlobal.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
key|string|
str_value|string|
duration|int|
npc_id|int|
char_id|int|
zone_id|int|

### Example

```perl
my $key = "test";
my $str_value = "test";
my $duration = 1;
my $npc_id = 1;
my $char_id = 1;
my $zone_id = 1;

quest::($key, $str_value, $duration, $npc_id, $char_id, $zone_id); # Returns void
```