EntityVariableExists.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
id||

### Example

```perl
my $id = 1;
my $val = $mob->EntityVariableExists($id);
quest::say($val); # Returns bool
```