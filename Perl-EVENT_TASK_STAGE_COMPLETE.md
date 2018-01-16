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

### Functionality Explained

EVENT_TASK_STAGE_COMPLETE is triggered when a task stage (either a task, or a task and activity) has been completed.  

### EVENT_TASK_STAGE_COMPLETE in use

```perl
# This example causes a world emote when a particular task and activity have been accomplished

sub EVENT_TASK_STAGE_COMPLETE {

     # Use == for numeric comparison to match task id "7" and activity id "4"
     if ($task_id == 7 && $activity_id == 4) {
          quest::we(15, "Finally, we have rid ourselves of the gnomes!");
     }
} 
```
Generated On 2018-01-15T22:07:30-08:00