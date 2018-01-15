MakePet.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spell_id|int|
pettype||
name|string|

### Example

```perl
my $spell_id = 1;
my $pettype = 1;
my $name = "test";

$mob->MakePet($spell_id, $pettype, $name); # Returns void
```