sends a client spell anim.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id||
seq||

### Example

```perl
my $spell_id = 1;
my $seq = 1;

$client->SendSpellAnim($spell_id, $seq); # Returns void
```