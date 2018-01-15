gets a mob equipment.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
material_slot||

### Example

```perl
my $material_slot = 1;
my $val = $mob->GetEquipment($material_slot);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00