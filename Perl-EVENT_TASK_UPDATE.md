EVENT_TASK_UPDATE
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
donecount|int|
activity_id|int|
task_id|int|
### Example
```perl
sub EVENT_TASK_UPDATE {
	quest::say($donecount); # returns int
	quest::say($activity_id); # returns int
	quest::say($task_id); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00