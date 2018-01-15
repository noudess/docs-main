SpellEffect.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
effect||
duration|int|
finish_delay||
zone_wide||
unk20||
perm_effect||
client||

### Example

```perl
my $effect = 1;
my $duration = 1;
my $finish_delay = 1;
my $zone_wide = 1;
my $unk20 = 1;
my $perm_effect = 1;
my $client = 1;

$mob->SpellEffect($effect, $duration, $finish_delay, $zone_wide, $unk20, $perm_effect, $client); # Returns void
```