sends a quest mail.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
to|string|
from|string|
subject|string|
message|string|

### Example

```perl
my $to = "test";
my $from = "test";
my $subject = "test";
my $message = "test";

quest::($to, $from, $subject, $message); # Returns void
```