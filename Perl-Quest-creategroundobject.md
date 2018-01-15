creategroundobject.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
item_id|int|
x|float|
y|float|
z|float|
heading|float|
decay_time|int|

### Example

```perl
my $item_id = 1;
my $x = 1;
my $y = 1;
my $z = 1;
my $heading = 1;
my $decay_time = 1;

quest::($item_id, $x, $y, $z, $heading, $decay_time); # Returns void
```