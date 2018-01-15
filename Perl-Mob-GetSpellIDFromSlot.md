gets a mob spell idf rom slot.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot|int|

### Example

```perl
my $slot = 1;
my $val = $mob->GetSpellIDFromSlot($slot);
quest::say($val); # Returns int
```