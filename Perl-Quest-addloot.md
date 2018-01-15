adds a quest loot.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
item_id|int|
charges|int|

### Example

```perl
my $item_id = 1;
my $charges = 1;

quest::($item_id, $charges); # Returns void
```