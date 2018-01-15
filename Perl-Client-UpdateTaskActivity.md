UpdateTaskActivity.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
TaskID||
ActivityID||
Count||
ignore_quest_update|bool|

### Example

```perl
my $TaskID = 1;
my $ActivityID = 1;
my $Count = 1;
my $ignore_quest_update = 1;

$client->UpdateTaskActivity($TaskID, $ActivityID, $Count, $ignore_quest_update); # Returns void
```