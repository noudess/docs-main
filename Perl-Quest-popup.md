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

quest::popup($window_title, $message, $popup_id, $buttons, $duration); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00