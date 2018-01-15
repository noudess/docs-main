adds a client alternate currency value.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
uint32 currency_id||int32 amount||
### Example

```perl
my $uint32 currency_id = 1;
my $int32 amount = 1;

$client->AddAlternateCurrencyValue($uint32 currency_id, $int32 amount); # Returns void
```