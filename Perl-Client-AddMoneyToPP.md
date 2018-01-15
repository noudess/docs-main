adds a client money to p p.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
copper|int|
silver|int|
gold|int|
platinum|int|
updateclient||

### Example

```perl
my $copper = 1;
my $silver = 1;
my $gold = 1;
my $platinum = 1;
my $updateclient = 1;

$client->AddMoneyToPP($copper, $silver, $gold, $platinum, $updateclient); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00