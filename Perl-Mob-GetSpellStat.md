gets a mob spell stat.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
itemid||
stat||
slot|int|

### Example

```perl
my $itemid = 1;
my $stat = 1;
my $slot = 1;
my $val = $mob->GetSpellStat($itemid, $stat, $slot);
quest::say($val); # Returns int
```