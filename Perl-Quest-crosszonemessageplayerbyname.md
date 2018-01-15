crosszonemessageplayerbyname.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
channel_id|int|
name|string|
message|string|

### Example

```perl
my $channel_id = 1;
my $name = "test";
my $message = "test";

quest::($channel_id, $name, $message); # Returns void
```