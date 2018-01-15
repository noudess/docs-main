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


Generated On 2018-01-15T13:04:48-08:00