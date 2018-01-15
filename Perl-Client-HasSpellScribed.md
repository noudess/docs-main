HasSpellScribed.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|

### Example

```perl
my $spell_id = 1;
my $val = $client->HasSpellScribed($spell_id);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00