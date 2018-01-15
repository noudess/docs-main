gets a client item ida t.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot_id||

### Example

```perl
my $slot_id = 1;
my $val = $client->GetItemIDAt($slot_id);
quest::say($val); # Returns int
```