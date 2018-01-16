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
### Functionality Explained

EVENT_ZONE is triggered when a player zones (not to be confused with perl EVENT_ENTERZONE).

### EVENT_ZONE in use

```perl
sub EVENT_ZONE {

     # Once you leave the zone, remove the compass mark (IE for adventure location)
     $client->ClearCompassMark();
}
```

Generated On 2018-01-15T22:07:30-08:00