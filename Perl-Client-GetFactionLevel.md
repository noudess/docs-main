gets a client faction level.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
char_id|int|
npc_id|int|
p_race||
p_class||
p_deity||
pFaction||
tnpc||

### Example

```perl
my $char_id = 1;
my $npc_id = 1;
my $p_race = 1;
my $p_class = 1;
my $p_deity = 1;
my $pFaction = 1;
my $tnpc = 1;
my $val = $client->GetFactionLevel($char_id, $npc_id, $p_race, $p_class, $p_deity, $pFaction, $tnpc);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00