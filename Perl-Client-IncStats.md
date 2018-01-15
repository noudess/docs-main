IncStats.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|
increase_val||

### Example

```perl
my $type = 1;
my $increase_val = 1;

$client->IncStats($type, $increase_val); # Returns void
```