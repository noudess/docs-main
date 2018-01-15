is a client task active.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
TaskID||

### Example

```perl
my $TaskID = 1;
my $val = $client->IsTaskActive($TaskID);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00