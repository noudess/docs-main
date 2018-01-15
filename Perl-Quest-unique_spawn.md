unique_spawn.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
npc_type_id|int|
grid_id|int|
int_unused|int|
x|float|
y|float|
z|float|
heading|float|

### Example

```perl
my $npc_type_id = 1;
my $grid_id = 1;
my $int_unused = 1;
my $x = 1;
my $y = 1;
my $z = 1;
my $heading = 1;
my $val = quest::unique_spawn($npc_type_id, $grid_id, $int_unused, $x, $y, $z, $heading);
quest::say($val); # Returns uint
```


Generated On 2018-01-15T13:04:48-08:00