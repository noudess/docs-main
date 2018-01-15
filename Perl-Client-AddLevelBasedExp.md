adds a client level based exp.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
exp_percentage||
max_level|int|

### Example

```perl
my $exp_percentage = 1;
my $max_level = 1;

$client->AddLevelBasedExp($exp_percentage, $max_level); # Returns void
```