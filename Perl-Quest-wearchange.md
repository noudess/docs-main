wearchange.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot|int|
texture_id|int|
hero_forge_model_id|int|
elite_material_id|int|

### Example

```perl
my $slot = 1;
my $texture_id = 1;
my $hero_forge_model_id = 1;
my $elite_material_id = 1;

quest::($slot, $texture_id, $hero_forge_model_id, $elite_material_id); # Returns void
```