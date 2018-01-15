sets a client custom item data.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot_id||
identifier||
value|int|

### Example

```perl
my $slot_id = 1;
my $identifier = 1;
my $value = 1;

$client->SetCustomItemData($slot_id, $identifier, $value); # Returns void
```