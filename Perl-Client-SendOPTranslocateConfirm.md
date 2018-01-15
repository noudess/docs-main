sends a client o p translocate confirm.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
Caster||
SpellID||

### Example

```perl
my $Caster = 1;
my $SpellID = 1;

$client->SendOPTranslocateConfirm($Caster, $SpellID); # Returns void
```