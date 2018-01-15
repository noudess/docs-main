crosszonesetentityvariablebynpctypeid.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
npc_type_id|int|
key|string|
str_value|string|

### Example

```perl
my $npc_type_id = 1;
my $key = "test";
my $str_value = "test";

quest::($npc_type_id, $key, $str_value); # Returns void
```