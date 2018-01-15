QuestReward.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
mob||
copper|int|
silver|int|
gold|int|
platinum|int|
itemid||
exp||
faction||

### Example

```perl
my $mob = 1;
my $copper = 1;
my $silver = 1;
my $gold = 1;
my $platinum = 1;
my $itemid = 1;
my $exp = 1;
my $faction = 1;

$client->QuestReward($mob, $copper, $silver, $gold, $platinum, $itemid, $exp, $faction); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00