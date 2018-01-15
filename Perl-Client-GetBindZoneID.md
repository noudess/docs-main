gets a client bind zone i d.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
index||

### Example

```perl
my $index = 1;
my $val = $client->GetBindZoneID($index);
quest::say($val); # Returns uint
```