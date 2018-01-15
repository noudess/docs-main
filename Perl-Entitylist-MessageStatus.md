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
my $... = 1;

$entitylist->MessageStatus($to_guilddbid, $to_minstatus, $type, $message, $...); # Returns void
```