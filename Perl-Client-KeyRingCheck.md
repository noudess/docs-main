KeyRingCheck.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
item_id|int|

### Example

```perl
my $item_id = 1;
my $val = $client->KeyRingCheck($item_id);
quest::say($val); # Returns bool
```