sets a mob a a.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
aa_id||
points||
charges|int|

### Example

```perl
my $aa_id = 1;
my $points = 1;
my $charges = 1;
my $val = $mob->SetAA($aa_id, $points, $charges);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00