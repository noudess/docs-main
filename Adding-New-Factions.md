To add a new faction on your server:

1. Add the new faction to the faction_list table.  Assign a value to base_value that indicates, aside from class/race/deity adjustments, how your new faction will regard everyone.

2. Add an entry to faction_base_data if you want the limits on earned faction to differ from -2000 to 2000.

|Faction Value|Faction CON|
|-------------------|-----------|
|1100 -> ABOVE  |ALLY|
|750 -> 1099 	|WARMLY|
|500 -> 749 	|KINDLY|
|100 -> 400 	|AMIABLE|
|0 -> 99 	|INDIFFERENT|
|-100 -> -1 	|APPREHENSIVE|
|-500 -> -101 	|DUBIOUS|
|-750 -> -501 	|THREATENLY|
|BELOW -> -751 	|SCOWLS|

3.  Decide if you want your faction to favor or dislike characters more of less based on their class, race or deity.  If so, add entries to faction_list_mod for your newly created faction.

4. Every NPC that you want to be on your new faction, will have to be on a new npc_faction that has a primary_faction set to your new faction from faction_list.  But unless all the NPCS that you want will all have the same faction hits when killed, you'll need a separate npc_faction for each tier of hits.  I hope we can factor this part out in a future work product.

5. If you want to assign faction hits or gains for killing any npc on your newly created npc_faction, add these entries to npc_faction_entries using your new npc_faction_id.

6.  If you want your newly created faction members to attack or assist certain other factions, add these entries to npc_faction_entries using your new npc_faction_id.

7. Assign the NPCs you want to your new npc_faction.

8. Restart the server for this to take effect.  We'll work on a live reloading mechanism.  