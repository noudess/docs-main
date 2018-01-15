adds a quest node.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
x|float|
y|float|
z|float|
best_z|float|
requested_id|int|

### Example

```perl
my $x = 1;
my $y = 1;
my $z = 1;
my $best_z = 1;
my $requested_id = 1;

quest::($x, $y, $z, $best_z, $requested_id); # Returns void
```