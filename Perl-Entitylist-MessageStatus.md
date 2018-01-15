MessageStatus.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
to_guilddbid||
to_minstatus||
type|int|
message|string|
...||

### Example

```perl
my $to_guilddbid = 1;
my $to_minstatus = 1;
my $type = 1;
my $message = "test";

$entity_list->MessageStatus($to_guilddbid, $to_minstatus, $type, $message, ...); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00