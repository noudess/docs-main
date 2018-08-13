# Controlling NPC aggro via faction tables.

Lets create a new faction.  For this example, the NPCs on this faction will be KOS to all PCs except Erudites, whom they will con amiable.  These NPCs will also attack other NPCs whom primary faction is Heretic.

1. Create the new base faction.
2. Create the new npc_faction.
3. Create how the new npc_faction reacts to other NPCS and PCs via npc_faction_entries.
4. Assign NPCs to the new npc_faction.
5. Since we want these NPCs to attack other NPCs (Heretics), change the npc_types entry for any NPC assigned to this faction so npc_aggro is set to 1.