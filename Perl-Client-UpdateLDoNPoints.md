UpdateLDoNPoints.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
points||
theme||

### Example

```perl
my $points = 1;
my $theme = 1;
my $val = $client->UpdateLDoNPoints($points, $theme);
quest::say($val); # Returns bool
```