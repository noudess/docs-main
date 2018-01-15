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


Generated On 2018-01-15T13:04:48-08:00