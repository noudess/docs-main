CheckLoS.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
mob||

### Example

```perl
my $mob = 1;
my $val = $mob->CheckLoS($mob);
quest::say($val); # Returns bool
```