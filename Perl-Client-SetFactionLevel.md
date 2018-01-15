sets a client faction level.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
char_id|int|
npc_id|int|
char_class||
char_race||
char_deity||

### Example

```perl
my $char_id = 1;
my $npc_id = 1;
my $char_class = 1;
my $char_race = 1;
my $char_deity = 1;

$client->SetFactionLevel($char_id, $npc_id, $char_class, $char_race, $char_deity); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00