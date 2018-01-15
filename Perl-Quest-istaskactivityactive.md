is a quest taskactivityactive.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
task_id|uint|
activity_id|uint|

### Example

```perl
my $task_id = 1;
my $activity_id = 1;
my $val = quest::($task_id, $activity_id);
quest::say($val); # Returns uint
```