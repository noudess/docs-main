is a questitem type.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|

### Example

```perl
my $type = 1;
my $val = $questitem->IsType($type);
quest::say($val); # Returns bool
```