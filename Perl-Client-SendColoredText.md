sends a client colored text.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
color|int|
message|string|

### Example

```perl
my $color = 1;
my $message = "test";

$client->SendColoredText($color, $message); # Returns void
```