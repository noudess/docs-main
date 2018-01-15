sets a client stats.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|
increase_val||

### Example

```perl
my $type = 1;
my $increase_val = 1;

$client->SetStats($type, $increase_val); # Returns void
```