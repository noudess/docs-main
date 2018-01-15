signalwith.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
npc_id|int|
signal_id|int|
wait_ms|int|

### Example

```perl
my $npc_id = 1;
my $signal_id = 1;
my $wait_ms = 1;

quest::signalwith($npc_id, $signal_id, $wait_ms); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00