crosszonesetentityvariablebyclient_name.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
client_name|string|
key|string|
str_value|string|

### Example

```perl
my $client_name = "test";
my $key = "test";
my $str_value = "test";

quest::($client_name, $key, $str_value); # Returns void
```