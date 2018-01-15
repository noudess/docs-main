sets a mob global.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
varname||
newvalue||
options|int|
duration|int|
other||

### Example

```perl
my $varname = 1;
my $newvalue = 1;
my $options = 1;
my $duration = 1;
my $other = 1;

$mob->SetGlobal($varname, $newvalue, $options, $duration, $other); # Returns void
```