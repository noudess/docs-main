CreateInstance.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
zone_name|string|
version|int|
duration|int|

### Example

```perl
my $zone_name = "test";
my $version = 1;
my $duration = 1;

quest::CreateInstance($zone_name, $version, $duration); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00