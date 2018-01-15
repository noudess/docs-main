npcfeature.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
str_value|string|
int_value|int|

### Example

```perl
my $str_value = "test";
my $int_value = 1;
my $val = quest::($str_value, $int_value);
quest::say($val); # Returns uint
```