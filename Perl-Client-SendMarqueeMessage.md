sends a client marquee message.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
type|int|
priority|int|
fade_in|int|
fade_out|int|
duration|int|
msg||

### Example

```perl
my $type = 1;
my $priority = 1;
my $fade_in = 1;
my $fade_out = 1;
my $duration = 1;
my $msg = 1;

$client->SendMarqueeMessage($type, $priority, $fade_in, $fade_out, $duration, $msg); # Returns void
```


Generated On 2018-01-15T13:04:48-08:00