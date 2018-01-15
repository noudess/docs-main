gets a client spell book slot by spell i d.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|

### Example

```perl
my $spell_id = 1;
my $val = $client->GetSpellBookSlotBySpellID($spell_id);
quest::say($val); # Returns int
```