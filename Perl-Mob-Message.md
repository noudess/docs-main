Message.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|
message|string|
...||

### Example

```perl
my $type = 1;
my $message = "test";
my $... = 1;

$mob->Message($type, $message, $...); # Returns void
```