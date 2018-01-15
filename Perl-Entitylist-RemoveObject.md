RemoveObject.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
delete_id||

### Example

```perl
my $delete_id = 1;
my $val = $entitylist->RemoveObject($delete_id);
quest::say($val); # Returns bool
```