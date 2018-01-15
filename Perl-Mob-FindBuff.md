FindBuff.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spellid||

### Example

```perl
my $spellid = 1;
my $val = $mob->FindBuff($spellid);
quest::say($val); # Returns bool
```