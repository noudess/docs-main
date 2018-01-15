gets a npc max damage.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
tlevel||

### Example

```perl
my $tlevel = 1;
my $val = $npc->GetMaxDamage($tlevel);
quest::say($val); # Returns uint
```