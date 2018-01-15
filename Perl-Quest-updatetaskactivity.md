updatetaskactivity.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
task_id|uint|
activity_id|uint|
count|int|
ignore_quest_update|bool|

### Example

```perl
my $task_id = 1;
my $activity_id = 1;
my $count = 1;
my $ignore_quest_update = 1;

quest::updatetaskactivity($task_id, $activity_id, $count, $ignore_quest_update); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00