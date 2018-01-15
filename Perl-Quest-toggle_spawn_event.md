toggle_spawn_event.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
event_id|uint|
is_enabled|bool|
is_strict|bool|
reset_base|bool|

### Example

```perl
my $event_id = 1;
my $is_enabled = 1;
my $is_strict = 1;
my $reset_base = 1;

quest::($event_id, $is_enabled, $is_strict, $reset_base); # Returns void
```