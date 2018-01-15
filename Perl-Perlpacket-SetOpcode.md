sets a perlpacket opcode.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
opcode||

### Example

```perl
my $opcode = 1;
my $val = $perlpacket->SetOpcode($opcode);
quest::say($val); # Returns bool
```


Generated On 2018-01-15T13:04:48-08:00