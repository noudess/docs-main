sets a quest guild.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
new_guild_id|unsigned long|
guild_rank_id|int|

### Example

```perl
my $new_guild_id = 1;
my $guild_rank_id = 1;

quest::($new_guild_id, $guild_rank_id); # Returns void
```