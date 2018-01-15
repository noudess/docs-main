MessageClose.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
sender||
skipsender||
dist||
type|int|
message|string|
...||

### Example

```perl
my $sender = 1;
my $skipsender = 1;
my $dist = 1;
my $type = 1;
my $message = "test";

$entity_list->MessageClose($sender, $skipsender, $dist, $type, $message, ...); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00