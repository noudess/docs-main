MessageGroup.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
sender||
skipclose||
type|int|
message|string|
...||

### Example

```perl
my $sender = 1;
my $skipclose = 1;
my $type = 1;
my $message = "test";

$entity_list->MessageGroup($sender, $skipclose, $type, $message, ...); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00