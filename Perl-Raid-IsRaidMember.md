is a raid raid member.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
name|string|

### Example

```perl
my $name = "test";
my $val = $raid->IsRaidMember($name);
quest::say($val); # Returns bool
```