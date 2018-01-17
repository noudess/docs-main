EVENT_TASK_UPDATE
### Exports
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

### Triggered

* Triggered when a player's task is updated.  
* Most existing quests handle this with EVENT_TASK_STAGE_COMPLETE or the goalcount in the Task System (stored in the database).


Generated On 2018-01-15T22:07:30-08:00