gets a client free spell book slot.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
start_slot||

### Example

```perl
my $start_slot = 1;
my $val = $client->GetFreeSpellBookSlot($start_slot);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00