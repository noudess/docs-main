EVENT_TASK_STAGE_COMPLETE
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
task_id|int|
activity_id|int|
### Example
```perl
sub EVENT_TASK_STAGE_COMPLETE {
	quest::say($task_id); # returns int
	quest::say($activity_id); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00