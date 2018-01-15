gets a mob global.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
varname||

### Example

```perl
my $varname = 1;
my $val = $mob->GetGlobal($varname);
quest::say($val); # Returns string
```