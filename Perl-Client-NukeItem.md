NukeItem.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
itemnum||
where_to_check||

### Example

```perl
my $itemnum = 1;
my $where_to_check = 1;
my $val = $client->NukeItem($itemnum, $where_to_check);
quest::say($val); # Returns uint
```


Generated On 2018-01-15T13:04:48-08:00