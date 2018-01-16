EVENT_COMBINE_FAILURE
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
recipe_id|int|
recipe_name|int|
### Example
```perl
sub EVENT_COMBINE_FAILURE {
	quest::say($recipe_id); # returns int
	quest::say($recipe_name); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00