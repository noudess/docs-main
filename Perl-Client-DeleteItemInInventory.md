DeleteItemInInventory.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot_id||
quantity|int|

### Example

```perl
my $slot_id = 1;
my $quantity = 1;

$client->DeleteItemInInventory($slot_id, $quantity); # Returns void
```