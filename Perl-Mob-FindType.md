FindType.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|
bOffensive||

### Example

```perl
my $type = 1;
my $bOffensive = 1;
my $val = $mob->FindType($type, $bOffensive);
quest::say($val); # Returns bool
```