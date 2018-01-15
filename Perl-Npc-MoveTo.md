MoveTo.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
mtx||
mty||
mtz||
mth||
saveguard|bool|

### Example

```perl
my $mtx = 1;
my $mty = 1;
my $mtz = 1;
my $mth = 1;
my $saveguard = 1;

$npc->MoveTo($mtx, $mty, $mtz, $mth, $saveguard); # Returns void
```