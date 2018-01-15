is a mob elite material item.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
material_slot||

### Example

```perl
my $material_slot = 1;
my $val = $mob->IsEliteMaterialItem($material_slot);
quest::say($val); # Returns uint
```