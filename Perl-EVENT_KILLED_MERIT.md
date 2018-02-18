EVENT_KILLED_MERIT is triggered on NPC death and applies to the group that did the most damage to the NPC (IE the group that got XP for the kill, assuming there was XP; or the group that gets loot rights to the NPC, assuming that there was loot).  Although not often used, this event gives you the opportunity to assign quest globals (for character flags) or update tasks.  

### Triggered

* On NPC death

### Examples

* In this example we update a task activity for all the players that took part in the kill.
* This example uses [quest::istaskactivityactive()](https://github.com/EQEmu/Server/wiki/Perl-Quest-istaskactivityactive) and [quest::updatetaskactivity()](https://github.com/EQEmu/Server/wiki/Perl-Quest-updatetaskactivity) perl functions.

```perl
sub EVENT_KILLED_MERIT {
     #:: If the group player has task activity 150
     if (quest::istaskactivityactive(150, 0)) {
          #:: Increment the task's activity by 1 step
          quest::updatetaskactivity(150, 0, 1);
     }
}
```

* In this example we add a quest global for all players who were in the group that killed the NPC
* Once we've created the quest global, we'll notify the player that they received credit (like a "character flag")

```perl
sub EVENT_KILLED_MERIT {
     #:: Get the name of the mob to use in the quest global
     my $slain = $npc->GetCleanName();
     #:: Set the quest global--this would apply to all group members
     $client->SetGlobal($slain,1,5,"F");
     #:: Display an emote message to each client in yellow to notify them that they received credit
     $client->Message(15, "You have received credit for killing ".$slain.".");
}
```