Retrieve a [client](client)'s account ID. An Account ID is wraps all characters together, and can be found in the database [Account](account).

### Example

```perl
sub EVENT_SAY {
	if($text=~/hail/i) {
		quest::say("Your account ID is: ".$client->AccountID().".";
	}
}
```