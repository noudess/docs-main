EVENT_COMMAND
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
text|int|
data|int|
langid|int|
### Example
```perl
sub EVENT_COMMAND {
	quest::say($text); # returns int
	quest::say($data); # returns int
	quest::say($langid); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00