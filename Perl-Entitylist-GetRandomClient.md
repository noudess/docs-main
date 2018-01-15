gets a entitylist random client.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
x|float|
y|float|
z|float|
distance|int|
excludeclient||

### Example

```perl
my $x = 1;
my $y = 1;
my $z = 1;
my $distance = 1;
my $excludeclient = 1;

$entitylist->GetRandomClient($x, $y, $z, $distance, $excludeclient); # Returns void
```