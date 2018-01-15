is a quest beneficial spell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|

### Example

```perl
my $spell_id = 1;
my $val = quest::($spell_id);
quest::say($val); # Returns uint
```