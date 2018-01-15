teleports a raid group.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
sender||
zoneID||
x|float|
y|float|
z|float|
heading|float|
gid||

### Example

```perl
my $sender = 1;
my $zoneID = 1;
my $x = 1;
my $y = 1;
my $z = 1;
my $heading = 1;
my $gid = 1;

$raid->TeleportGroup($sender, $zoneID, $x, $y, $z, $heading, $gid); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00