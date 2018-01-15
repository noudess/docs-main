sets a quest target.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
target_enum|string|
target_id|int|

### Example

```perl
my $target_enum = "test";
my $target_id = 1;

quest::($target_enum, $target_id); # Returns void
```