gets a perlpacket byte.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
pos||

### Example

```perl
my $pos = 1;
my $val = $perlpacket->GetByte($pos);
quest::say($val); # Returns uint
```