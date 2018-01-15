GrantAlternateAdvancementAbility.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
aa_id||
points||
ignore_cost||

### Example

```perl
my $aa_id = 1;
my $points = 1;
my $ignore_cost = 1;
my $val = $client->GrantAlternateAdvancementAbility($aa_id, $points, $ignore_cost);
quest::say($val); # Returns bool
```