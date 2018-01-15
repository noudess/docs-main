is a group group member.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
client||

### Example

```perl
my $client = 1;
my $val = $group->IsGroupMember($client);
quest::say($val); # Returns bool
```