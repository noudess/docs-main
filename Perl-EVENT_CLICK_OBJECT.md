EVENT_CLICK_OBJECT is triggered when a player clicks on an object.  Note the similarity between this event and [Perl EVENT_CLICKDOOR](https://github.com/EQEmu/Server/wiki/Perl-EVENT_CLICKDOOR), since it is easy to confuse a door object (like a Plane of Knowledge Book) with Objects (IE Pottery wheels, Brew Barrels, etc.).

You would likely use this event in the zone player.pl (or global_player.pl) files.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
objectid|int|
clicker_id|int|
### Example
```perl
sub EVENT_CLICK_OBJECT {
	quest::say($objectid); # returns int
	quest::say($clicker_id); # returns int
}
```

### Triggered

* When a client clicks on an object

### Example

* In this example we add flavor text for player who clicks on the Ogre cultural forge

```perl
sub EVENT_CLICK_OBJECT {
     #:: Match to the ogre cultural forge in Oggok by object ID
     if ($objectid == 1075) {
          #:: Check to see if the player who clicked is a race other than Ogre
          if ($race ne "Ogre") {
               #:: Send the client a message in color 1 (gray)
               $client->Message(1,"The foul stench of Ogre overwhelms you as you open the forge...you stagger away, unable to use it.");
          } else {
               $client->Message(1,"Mmmm--dis smells just like home.");
          }
     }
}
```

Generated On 2018-01-15T22:07:30-08:00