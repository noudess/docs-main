adds a npc a i spell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
priority|int|
spell_id|int|
type|int|
mana_cost||
recast_delay||
resist_adjust||

### Example

```perl
my $priority = 1;
my $spell_id = 1;
my $type = 1;
my $mana_cost = 1;
my $recast_delay = 1;
my $resist_adjust = 1;

$npc->AddAISpell($priority, $spell_id, $type, $mana_cost, $recast_delay, $resist_adjust); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00