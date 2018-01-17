EVENT_ZONE
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
target_zone_id|int|
### Example
```perl
sub EVENT_ZONE {
	quest::say($target_zone_id); # returns int
}
```
### Triggered

* When a player zones (not to be confused with perl EVENT_ENTERZONE).

### Example

* This example removes the compass mark (IE for adventure location) when you zone out.

```perl
sub EVENT_ZONE {
     $client->ClearCompassMark();
}
```

Generated On 2018-01-15T22:07:30-08:00