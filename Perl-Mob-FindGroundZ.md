FindGroundZ.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
new_x||
new_y||
z_offset||

### Example

```perl
my $new_x = 1;
my $new_y = 1;
my $z_offset = 1;
my $val = $mob->FindGroundZ($new_x, $new_y, $z_offset);
quest::say($val); # Returns double
```