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