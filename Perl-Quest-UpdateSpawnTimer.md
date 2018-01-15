UpdateSpawnTimer.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spawn2_id|uint|
updated_time_till_repop|uint|

### Example

```perl
my $spawn2_id = 1;
my $updated_time_till_repop = 1;

quest::($spawn2_id, $updated_time_till_repop); # Returns void
```