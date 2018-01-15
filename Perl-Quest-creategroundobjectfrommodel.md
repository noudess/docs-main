creategroundobjectfrommodel.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
modelname|string|
x|float|
y|float|
z|float|
heading|float|
object_type|int|
decay_time|int|

### Example

```perl
my $modelname = "test";
my $x = 1;
my $y = 1;
my $z = 1;
my $heading = 1;
my $object_type = 1;
my $decay_time = 1;

quest::creategroundobjectfrommodel($modelname, $x, $y, $z, $heading, $object_type, $decay_time); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00