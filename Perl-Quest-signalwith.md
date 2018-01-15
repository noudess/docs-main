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

quest::($npc_id, $signal_id, $wait_ms); # Returns void
```