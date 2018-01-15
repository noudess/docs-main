gets a client corpse i d.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
corpse||

### Example

```perl
my $corpse = 1;
my $val = $client->GetCorpseID($corpse);
quest::say($val); # Returns int
```