MaxSkill.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
skillid||
class||
level|int|

### Example

```perl
my $skillid = 1;
my $class = 1;
my $level = 1;
my $val = $client->MaxSkill($skillid, $class, $level);
quest::say($val); # Returns uint
```