CheckNPCFactionAlly.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
other_faction||

### Example

```perl
my $other_faction = 1;
my $val = $npc->CheckNPCFactionAlly($other_faction);
quest::say($val); # Returns int
```