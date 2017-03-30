EntityList is a class exported to Lua that represent the EntityList object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
entity_list.null -- Returns true if this object is null
entity_list.valid -- Returns true if this object is not null
```

### Member Functions
```
EntityList() -- Creates a null EntityList
Mob GetMobID(Integer id);
Mob GetMob(String name);
Mob GetMob(Integer id);
Mob GetMobByNpcTypeID(Integer npc_type);
NPC GetNPCByID(Integer id);
NPC GetNPCByNPCTypeID(Integer npc_type);
Bool IsMobSpawnedByNpcTypeID(Interger npc_type);
Client GetClientByName(String name);
Client GetClientByAccID(Integer acct_id);
Client GetClientByID(Integer id);
Client GetClientByCharID(Integer char_id);
Client GetClientByWID(Integer wid);
Object GetObjectByID(Integer id);
Object GetObjectByDBID(Integer db_id);
Door GetDoorsByID(Integer id);
Door GetDoorsByDBID(Integer db_id);
Door GetDoorsByDoorID(Integer door_id);
Door FindDoor(Integer id);
Group GetGroupByMob(Mob mob);
Group GetGroupByClient(Client client);
Group GetGroupByID(Integer id);
Group GetGroupByLeaderName(String name);
Raid GetRaidByID(Integer id);
Raid GetRaidByClient(Client client);
Corpse GetCorpseByOwner(Client client);
Corpse GetCorpseByID(Integer id);
Corpse GetCorpseByName(String name);
Spawn GetSpawnByID(Integer id);
Void ClearClientPetitionQueue();
Boolean CanAddHateForMob(Mob p);
Void Message(Integer guild_dbid, Integer type, String message);
Void MessageStatus(Integer guild_dbid, Integer min_status, Integer type, String message);
Void MessageClose(Mob sender, Boolean skip_sender, Real dist, Integer type, String message);
Void RemoveFromTargets(Mob mob);
Void RemoveFromTargets(Mob mob, bool RemoveFromXTargets);
Void ReplaceWithTarget(Mob target, Mob new_target);
Void OpenDoorsNear(NPC opener);
String MakeNameUnique(String name);
String RemoveNumbers(String name);
Void SignalMobsByNPCID(Integer npc_id, Integer signal);
Integer DeleteNPCCorpses();
Integer DeletePlayerCorpses();
Void HalveAggro(Mob who);
Void DoubleAggro(Mob who);
Void ClearFeignAggro(Mob who);
Boolean Fighting(Mob who);
Void RemoveFromHateLists(Mob who);
Void RemoveFromHateLists(Mob who, Boolean set_to_one);
Void MessageGroup(Mob who, Boolean skip_close, Integer type, String message);
Client GetRandomClient(Real x, Real y, Real z, Real dist); --note "dist" in this case is sqrt.  so 1,000 range needs to be 1,000,000
Client GetRandomClient(Real x, Real y, Real z, Real dist, Client exclude);
Mob_List GetMobList();
Client_List GetClientList();
NPC_List GetNPCList();
Corpse_List GetCorpseList();
Object_List GetObjectList();
Doors_List GetDoorsList();
Spawn_List GetSpawnList();
Void SignalAllClients(Integer signal);
Void ChannelMessage(Mob from, Integer type, String msg, Integer language); 
```

Mob_List, Client_List, NPC_List, Corpse_List, Object_List, Doors_List and Spawn_List are Lua tables that have an entries field that is a table that contains the entity list of all those types.