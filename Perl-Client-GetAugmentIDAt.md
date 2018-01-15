gets a client augment ida t.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
slot_id||
augslot||

### Example

```perl
my $slot_id = 1;
my $augslot = 1;
my $val = $client->GetAugmentIDAt($slot_id, $augslot);
quest::say($val); # Returns int
```


Generated On 2018-01-15T13:04:48-08:00