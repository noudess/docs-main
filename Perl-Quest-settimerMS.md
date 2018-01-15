sets a quest timer m s.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
timer_name|string|
milliseconds|int|

### Example

```perl
my $timer_name = "test";
my $milliseconds = 1;

quest::($timer_name, $milliseconds); # Returns void
```