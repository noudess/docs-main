EVENT_AGGRO_SAY
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
data|int|
text|int|
langid|int|
### Example
```perl
sub EVENT_AGGRO_SAY {
	quest::say($data); # returns int
	quest::say($text); # returns int
	quest::say($langid); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00