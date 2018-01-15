CheckIncreaseSkill.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
skillid||
chancemodi||

### Example

```perl
my $skillid = 1;
my $chancemodi = 1;
my $val = $client->CheckIncreaseSkill($skillid, $chancemodi);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00