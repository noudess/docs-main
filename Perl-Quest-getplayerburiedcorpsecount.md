gets a quest playerburiedcorpsecount.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
char_id|int|

### Example

```perl
my $char_id = 1;
my $val = quest::($char_id);
quest::say($val); # Returns uint
```