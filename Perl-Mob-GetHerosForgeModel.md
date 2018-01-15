gets a mob heros forge model.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
material_slot||

### Example

```perl
my $material_slot = 1;
my $val = $mob->GetHerosForgeModel($material_slot);
quest::say($val); # Returns int
```