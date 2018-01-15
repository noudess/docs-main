SlotConvert2.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot|int|

### Example

```perl
my $slot = 1;
my $val = $client->SlotConvert2($slot);
quest::say($val); # Returns uint
```