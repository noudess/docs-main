popup.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
window_title|string|
message|string|
popup_id|int|
buttons|int|
duration|int|

### Example

```perl
my $window_title = "test";
my $message = "test";
my $popup_id = 1;
my $buttons = 1;
my $duration = 1;

quest::($window_title, $message, $popup_id, $buttons, $duration); # Returns void
```