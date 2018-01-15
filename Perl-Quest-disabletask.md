disabletask.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
task_id1|int|
task_id2|int|
...||
task_id10|int|

### Example

```perl
my $task_id1 = 1;
my $task_id2 = 1;
my $... = 1;
my $task_id10 = 1;

quest::($task_id1, $task_id2, $..., $task_id10); # Returns void
```