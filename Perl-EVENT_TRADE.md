EVENT_TRADE
### Arguments
**Name**|**Type**|**Description**
:-----|:-----|:-----
copper|int|
silver|int|
gold|int|
platinum|int|
### Example
```perl
sub EVENT_TRADE {
	quest::say($copper); # returns int
	quest::say($silver); # returns int
	quest::say($gold); # returns int
	quest::say($platinum); # returns int
}
```

Generated On 2018-01-15T22:01:49-08:00