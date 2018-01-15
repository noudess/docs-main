qs_player_event.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
char_id|int|
message|string|

### Example

```perl
my $char_id = 1;
my $message = "test";

quest::($char_id, $message); # Returns void
```