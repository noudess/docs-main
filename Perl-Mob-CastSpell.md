CastSpell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
target_id|int|
slot|int|

### Example

```perl
my $spell_id = 1;
my $target_id = 1;
my $slot = 1;

$mob->CastSpell($spell_id, $target_id, $slot); # Returns void
```