CheckHealAggroAmount.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spellid||
possible_heal_amt||

### Example

```perl
my $spellid = 1;
my $possible_heal_amt = 1;
my $val = $mob->CheckHealAggroAmount($spellid, $possible_heal_amt);
quest::say($val); # Returns uint
```