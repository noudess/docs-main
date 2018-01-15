DoMeleeSkillAttackDmg.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
target||
weapon_damage||
skill||
chance_mod||
focus||
CanRiposte||

### Example

```perl
my $target = 1;
my $weapon_damage = 1;
my $skill = 1;
my $chance_mod = 1;
my $focus = 1;
my $CanRiposte = 1;

$mob->DoMeleeSkillAttackDmg($target, $weapon_damage, $skill, $chance_mod, $focus, $CanRiposte); # Returns void
```