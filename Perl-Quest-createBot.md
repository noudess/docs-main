createBot.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
firstname|string|
lastname|string|
level|int|
race_id|int|
class_id|int|
gender_id|int|

### Example

```perl
my $firstname = "test";
my $lastname = "test";
my $level = 1;
my $race_id = 1;
my $class_id = 1;
my $gender_id = 1;
my $val = quest::createBot($firstname, $lastname, $level, $race_id, $class_id, $gender_id);
quest::say($val); # Returns uint
```


Generated On 2018-01-15T13:04:48-08:00