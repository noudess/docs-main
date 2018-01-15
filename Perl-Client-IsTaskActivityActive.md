is a client task activity active.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
TaskID||
ActivityID||

### Example

```perl
my $TaskID = 1;
my $ActivityID = 1;
my $val = $client->IsTaskActivityActive($TaskID, $ActivityID);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00