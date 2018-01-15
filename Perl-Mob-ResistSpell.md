ResistSpell.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
ressit_type||
spell_id|int|
caster||

### Example

```perl
my $ressit_type = 1;
my $spell_id = 1;
my $caster = 1;
my $val = $mob->ResistSpell($ressit_type, $spell_id, $caster);
quest::say($val); # Returns double
```