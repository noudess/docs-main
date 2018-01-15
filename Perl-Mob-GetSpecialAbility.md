gets a mob special ability.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
special_ability||

### Example

```perl
my $special_ability = 1;
my $val = $mob->GetSpecialAbility($special_ability);
quest::say($val); # Returns int
```