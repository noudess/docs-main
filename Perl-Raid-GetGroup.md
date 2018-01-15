gets a raid group.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
name|string|

### Example

```perl
my $name = "test";
my $val = $raid->GetGroup($name);
quest::say($val); # Returns uint
```