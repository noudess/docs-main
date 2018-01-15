UseDiscipline.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
target||

### Example

```perl
my $spell_id = 1;
my $target = 1;
my $val = $client->UseDiscipline($spell_id, $target);
quest::say($val); # Returns bool
```