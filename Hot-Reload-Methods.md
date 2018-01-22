
This page explains how different assets on the server can be reloaded, what commands can be used etc.

### Alternate Currency Data

* In game command #reloadstatic - will reload alternate currency data from the [[alternate_currency]] table for just the zone the command was executed in

### Doors

* In game command **#reloadstatic** - will reload doors from the [[doors]] table for the respective zone and instance

### Ground Spawns

* In game command **#reloadstatic** - will reload ground spawns from the [[ground_spawns]] table for the respective zone and instance

### NPC Emotes

* While emotes don't HAVE to be database driven (most custom servers will just use scripts) - there is an option to reload the database driven emotes
* In game command **#reloadstatic** - will reload database driven emote data from the [[npc_emotes]] table for just the zone the command was executed in

### Objects

* In game command **#reloadstatic** - will reload objects from the [[objects]] table for the respective zone and instance

### Perl Event Exports

* In game command **#reloadperlexportsettings** will reload all export settings from the [[perl_event_export_settings]] table and this will take affect for **all current running zones**

### Quests 

* In game command **#rq** or **#reloadquest** will reload all quest scripts for the zone you are in, LUA or Perl
* Server-wide in game command **#reloadworld** will perform a quest reload for all zones, however keep in mind this does a repop as well

### Rules

* In game command **#reloadallrules** will reload rules for all running zone processes and the world process

### Traps

* In game command **#reloadstatic** - will reload traps from the [[traps]] table for the respective zone and instance
* In game comand **#reloadtraps** will also reload traps without reloading everything else that **#reloadstatic** hits

### Zone Points

* In game command **#reloadstatic** - will zone points from the [[zone_points]] table for the respective zone and instance - note this may not work for all clients

### Zone Data

* Sometimes you want to reload the [[zone]] table data, this is done via using #zheader [zoneshortname]. If you're in Nexus, use **#zheader nexus**
* This will resend the zone header packet to the client to update fog / sky / gravity / data / etc