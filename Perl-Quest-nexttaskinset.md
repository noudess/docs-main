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
my $val = quest::($task_set, $task_id);
quest::say($val); # Returns int
```