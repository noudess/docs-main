# Controlling NPC aggro via faction tables.

Lets create a new faction.  For this example, the NPCs on this faction will be KOS to all PCs except Erudites, whom they will con amiable.  These NPCs will also attack other NPCs whom primary faction is Heretic.  If anyone kills these NPCs, we will have them lose 10 points of faction with their faction (the new one we're creating) and gain 5 points with Heretic.

1. Create the new base faction to [faction_list](https://github.com/EQEmu/Server/wiki/faction_list).
2. Create the new [npc_faction](https://github.com/EQEmu/Server/wiki/npc_faction).
3. Create new [faction_list_mod](https://github.com/EQEmu/Server/wiki/faction_list_mod) entries to account for the Erudite loving aspect.
4. Create how the new npc_faction reacts to other NPCS and PCs via [npc_faction_entries](https://github.com/EQEmu/Server/wiki/npc_faction_entries).
5. Added more npc_faction_entries for the faction hits if you kill these NPCs.
6. Assign NPCs to the new npc_faction in the npc_types table.
7. Since we want these NPCs to attack other NPCs (Heretics), change the npc_types entry for any NPC assigned to this faction so npc_aggro is set to 1.