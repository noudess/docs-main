CheckLoSToLoc.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
loc_x||
loc_y||
loc_z||
mob_size||

### Example

```perl
my $loc_x = 1;
my $loc_y = 1;
my $loc_z = 1;
my $mob_size = 1;
my $val = $mob->CheckLoSToLoc($loc_x, $loc_y, $loc_z, $mob_size);
quest::say($val); # Returns bool
```