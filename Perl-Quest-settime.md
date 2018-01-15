sets a quest time.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
new_hour|int|
new_min|int|
update_world|int|

### Example

```perl
my $new_hour = 1;
my $new_min = 1;
my $update_world = 1;

quest::($new_hour, $new_min, $update_world); # Returns void
```