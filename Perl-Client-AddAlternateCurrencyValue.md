adds a client alternate currency value.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
currency_id||amount||
### Example

```perl
my $currency_id = 1;
my $amount = 1;

$client->AddAlternateCurrencyValue($currency_id, $amount); # Returns void
```