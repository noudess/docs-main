nexttaskinset.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
task_set|int|
task_id|uint|

### Example

```perl
my $task_set = 1;
my $task_id = 1;
my $val = quest::nexttaskinset($task_set, $task_id);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00