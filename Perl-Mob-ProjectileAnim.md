ProjectileAnim.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
mob||
item_id|int|
IsArrow||
speed||
angle||
tilt||
arc||

### Example

```perl
my $mob = 1;
my $item_id = 1;
my $IsArrow = 1;
my $speed = 1;
my $angle = 1;
my $tilt = 1;
my $arc = 1;

$mob->ProjectileAnim($mob, $item_id, $IsArrow, $speed, $angle, $tilt, $arc); # Returns void
```