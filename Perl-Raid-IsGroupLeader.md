is a raid group leader.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
who||

### Example

```perl
my $who = 1;
my $val = $raid->IsGroupLeader($who);
quest::say($val); # Returns bool
```