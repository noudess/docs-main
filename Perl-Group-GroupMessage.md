GroupMessage.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
sender||
language||
message|string|

### Example

```perl
my $sender = 1;
my $language = 1;
my $message = "test";

$group->GroupMessage($sender, $language, $message); # Returns void
```