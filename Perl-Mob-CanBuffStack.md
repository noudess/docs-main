CanBuffStack.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
spellid||
caster_level||
iFailIfOverwrite||

### Example

```perl
my $spellid = 1;
my $caster_level = 1;
my $iFailIfOverwrite = 1;
my $val = $mob->CanBuffStack($spellid, $caster_level, $iFailIfOverwrite);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00