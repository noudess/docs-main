is a group leader.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
leadertest||

### Example

```perl
my $leadertest = 1;
my $val = $group->IsLeader($leadertest);
quest::say($val); # Returns bool
```