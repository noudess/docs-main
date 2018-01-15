CheckAggroAmount.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spellid||

### Example

```perl
my $spellid = 1;
my $val = $mob->CheckAggroAmount($spellid);
quest::say($val); # Returns uint
```