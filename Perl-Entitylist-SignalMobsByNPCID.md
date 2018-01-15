SignalMobsByNPCID.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
npc_type||
signal_id|int|

### Example

```perl
my $npc_type = 1;
my $signal_id = 1;

$entitylist->SignalMobsByNPCID($npc_type, $signal_id); # Returns void
```