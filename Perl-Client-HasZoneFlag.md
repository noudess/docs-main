HasZoneFlag.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
zone_id|int|

### Example

```perl
my $zone_id = 1;
my $val = $client->HasZoneFlag($zone_id);
quest::say($val); # Returns bool
```