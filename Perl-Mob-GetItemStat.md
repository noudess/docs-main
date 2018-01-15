gets a mob item stat.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
itemid||
stat||

### Example

```perl
my $itemid = 1;
my $stat = 1;
my $val = $mob->GetItemStat($itemid, $stat);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00