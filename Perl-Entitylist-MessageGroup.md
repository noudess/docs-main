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
my $... = 1;

$entitylist->MessageGroup($sender, $skipclose, $type, $message, $...); # Returns void
```