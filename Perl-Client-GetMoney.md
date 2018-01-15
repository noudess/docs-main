gets a client money.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|
subtype||

### Example

```perl
my $type = 1;
my $subtype = 1;
my $val = $client->GetMoney($type, $subtype);
quest::say($val); # Returns double
```


Generated On 2018-01-15T13:04:48-08:00