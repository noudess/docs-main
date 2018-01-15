gets a quest guildnamebyid.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
guild_id||

### Example

```perl
my $guild_id = 1;
my $val = quest::($guild_id);
quest::say($val); # Returns string
```