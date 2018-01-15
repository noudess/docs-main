sets a quest timer.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
timer_name|string|
seconds|int|

### Example

```perl
my $timer_name = "test";
my $seconds = 1;

quest::($timer_name, $seconds); # Returns void
```