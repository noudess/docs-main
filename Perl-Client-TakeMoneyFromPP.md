TakeMoneyFromPP.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
copper|int|
updateclient||

### Example

```perl
my $copper = 1;
my $updateclient = 1;
my $val = $client->TakeMoneyFromPP($copper, $updateclient);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00