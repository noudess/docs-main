EVENT_AGGRO_SAY is triggered when an NPC is in combat, a player has that NPC targeted, and says something. This is not a widely used function, as this particular scenario did not exist in EQ.  You can use this function for easy statistics or information from a test NPC during a fight--perhaps consider the training dummy NPCs in The Arena.

### Exports
**Name**|**Type**|**Description**
:-----|:-----|:-----
data|int|
text|int|
langid|int|
### Example
```perl
sub EVENT_AGGRO_SAY {
	quest::say($data); # returns int
	quest::say($text); # returns int
	quest::say($langid); # returns int
}
```

### Triggered

* When a player says something to a targeted, aggro NPC.

### Example

* In this example, the NPC will respond to a player saying "hate" while in combat and will report back the amount of hate generated and damage dealt to the NPC by the player.  

```perl
sub EVENT_AGGRO_SAY {
     #:: Match the say message like "hate", the "i" is for case-insensitive.
     if ($text=~/hate/i) {
          #:: create an array of entities on the NPC's hate list including the entity name, hate and damage
          my @hatelist = $npc->GetHateList();
          foreach $ent (@hatelist) {
               my $h_ent = $ent->GetEnt();
               my $h_dmg = $ent->GetDamage();
               my $h_hate = $ent->GetHate();
               #:: Report the hate and damage
               if ($h_ent) {
                    my $h_ent_name = $h_ent->GetCleanName();
                    quest::say("$h_ent_name is on my hate list with $h_hate hate and $h_dmg damage.");
               }
          }
     }
}
```

Generated On 2018-01-15T22:07:30-08:00