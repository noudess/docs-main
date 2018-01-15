gets a client task activity done count.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
TaskID||
ActivityID||

### Example

```perl
my $TaskID = 1;
my $ActivityID = 1;
my $val = $client->GetTaskActivityDoneCount($TaskID, $ActivityID);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00