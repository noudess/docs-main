traindiscs.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
max_level|int|
min_level|int|

### Example

```perl
my $max_level = 1;
my $min_level = 1;
my $val = quest::($max_level, $min_level);
quest::say($val); # Returns uint
```