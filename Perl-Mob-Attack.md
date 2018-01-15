Attack.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
other||
Hand||

### Example

```perl
my $other = 1;
my $Hand = 1;
my $val = $mob->Attack($other, $Hand);
quest::say($val); # Returns bool
```