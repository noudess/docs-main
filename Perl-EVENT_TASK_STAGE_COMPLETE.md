
EVENT_TASK_STAGE_COMPLETE
### Exports
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

### Triggered

* When a task stage (either a task, or a task and activity) has been completed.  

### Examples

* This triggers a world emote when a particular task and activity have been progressed

```perl
sub EVENT_TASK_STAGE_COMPLETE {
     if ($task_id == 7 && $activity_id == 4) {

	  #::: World Emote
          quest::we(15, "Finally, we have rid ourselves of the gnomes!");
     }
} 
```
Generated On 2018-01-15T22:07:30-08:00