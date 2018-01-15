is a raid leader.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
name|string|

### Example

```perl
my $name = "test";
my $val = $raid->IsLeader($name);
quest::say($val); # Returns bool
```