gets a client disc slot by spell i d.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|

### Example

```perl
my $spell_id = 1;
my $val = $client->GetDiscSlotBySpellID($spell_id);
quest::say($val); # Returns int
```