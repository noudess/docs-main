gets a client a a level.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
aaskillid||

### Example

```perl
my $aaskillid = 1;
my $val = $client->GetAALevel($aaskillid);
quest::say($val); # Returns uint
```