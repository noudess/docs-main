adds a client alternate currency value.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
currency_id|uint32|
amount|int32|
### Example

```perl
my currency_id = 1;
my amount = 1;
quest::say($client->AddAlternateCurrencyValue(currency_id, amount));
```