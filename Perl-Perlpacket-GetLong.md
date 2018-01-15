gets a perlpacket long.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
pos||

### Example

```perl
my $pos = 1;
my $val = $perlpacket->GetLong($pos);
quest::say($val); # Returns uint
```