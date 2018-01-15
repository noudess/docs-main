gets a mob equipment color.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
material_slot||

### Example

```perl
my $material_slot = 1;
my $val = $mob->GetEquipmentColor($material_slot);
quest::say($val); # Returns int
```