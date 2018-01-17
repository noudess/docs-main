EVENT_SAY
### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
data|int|
text|int|
langid|int|
### Example
```perl
sub EVENT_SAY {
	quest::say($data); # returns int
	quest::say($text); # returns int
	quest::say($langid); # returns int
}
```

### Triggered

* When a PC targets and speaks to an NPC.

### Examples

* This example is a response to a "hail"

```perl
sub EVENT_SAY {
     #::: Checks if the text is like "Hail", the "i" is for case-insensitive.
     if ($text=~/Hail/i) {
          quest::say("Hello, $name!");
     }
}
```

* This example additionally checks the language of the "hail", and will only respond to text in that language.

```perl
sub EVENT_SAY {
     #::: Checks to see if the language is Thieves Cant (language ID 10)
     if ($langid == 10) {
          #::: Checks if the text is like "Hail", the "i" is for case-insensitive.
          if ($text=~/Hail/i) {
               # Respond, using the same language
               quest::say("Hello, $name!",10);
          }
     }
}
```


Generated On 2018-01-15T22:07:30-08:00