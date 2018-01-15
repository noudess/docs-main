Message.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
to_guilddbid||
type|int|
message|string|
...||

### Example

```perl
my $to_guilddbid = 1;
my $type = 1;
my $message = "test";
my $... = 1;

$entitylist->Message($to_guilddbid, $type, $message, $...); # Returns void
```