ScribeSpell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
slot|int|
update_client||

### Example

```perl
my $spell_id = 1;
my $slot = 1;
my $update_client = 1;

$client->ScribeSpell($spell_id, $slot, $update_client); # Returns void
```