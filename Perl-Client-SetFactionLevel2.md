sets a client faction level2.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
char_id|int|
faction_id||
char_class||
char_race||
char_deity||
value|int|
temp|int|

### Example

```perl
my $char_id = 1;
my $faction_id = 1;
my $char_class = 1;
my $char_race = 1;
my $char_deity = 1;
my $value = 1;
my $temp = 1;

$client->SetFactionLevel2($char_id, $faction_id, $char_class, $char_race, $char_deity, $value, $temp); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00