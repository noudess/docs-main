ValidMobByNpcTypeID.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
get_id||

### Example

```perl
my $get_id = 1;
my $val = $entitylist->ValidMobByNpcTypeID($get_id);
quest::say($val); # Returns bool
```