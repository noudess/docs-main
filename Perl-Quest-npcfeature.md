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
my $val = quest::npcfeature($str_value, $int_value);
quest::say($val); # Returns uint
```


Generated On 2018-01-15T13:04:48-08:00