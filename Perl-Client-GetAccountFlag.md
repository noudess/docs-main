gets a client account flag.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
flag||

### Example

```perl
my $flag = 1;
my $val = $client->GetAccountFlag($flag);
quest::say($val); # Returns string
```