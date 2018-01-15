gets a perlpacket short.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
pos||

### Example

```perl
my $pos = 1;
my $val = $perlpacket->GetShort($pos);
quest::say($val); # Returns uint
```