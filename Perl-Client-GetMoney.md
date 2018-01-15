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