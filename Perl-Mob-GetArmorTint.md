gets a mob armor tint.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
material_slot||

### Example

```perl
my $material_slot = 1;
my $val = $mob->GetArmorTint($material_slot);
quest::say($val); # Returns int
```