To add a new faction on your server:

1. Add the new faction to the faction_list table.  Assign a value to base_value that indicates, aside from class/race/deity adjustments, how your new faction will regard everyone.

|Faction Value|Faction CON|
|-------------------|-----------|
|1101 -> ABOVE  |ALLY|
|701 -> 1100 	|WARMLY|
|401 -> 700 	|KINDLY|
|101 -> 400 	|AMIABLE|
|0 -> 100 	|INDIFFERENT|
|-100 -> -1 	|APPREHENSIVE|
|-700 -> -101 	|DUBIOUS|
|-999 -> -701 	|THREATENLY|
|-1000 -> BELOW 	|SCOWLS|

2.  Decide if you want your faction to favor or dislike characters more of less based on their class, race or deity.  If so, add entries to faction_list_mod for your newly created faction.

3. Every NPC that you want to be on your new faction, will have to be on a new npc_faction that has a primary_faction set to your new faction from faction_list.  But unless all the NPCS that you want will all have the same faction hits when killed, you'll need a separate npc_faction for each tier of hits.  I hope we can factor this part out in a future work product.

4. If you want to assign faction hits or gains for killing any npc on your newly created npc_faction, add these entries to npc_faction_entries using your new npc_faction_id.

5.  If you want your newly created faction members to attack or assist certain other factions, add these entries to npc_faction_entries using your new npc_faction_id.

6. Assign the NPCs you want to your new npc_faction.

7. Restart the server for this to take effect.  We'll work on a live reloading mechanism.  