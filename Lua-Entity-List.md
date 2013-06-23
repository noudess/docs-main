Lua_EntityList is a class exported to Lua that represent the EntityList object from EQEmu.

### Properties
```
entity_list.null -- Returns true if this object is null
entity_list.valid -- Returns true if this object is not null
```

### Member Functions
```
EntityList() -- Creates a null EntityList
Lua_Mob GetMobID(int id);
Lua_Mob GetMob(const char *name);
Lua_Mob GetMob(int id);
Lua_Mob GetMobByNpcTypeID(int npc_type);
Lua_NPC GetNPCByID(int id);
Lua_NPC GetNPCByNPCTypeID(int npc_type);
Lua_Client GetClientByName(const char *name);
Lua_Client GetClientByAccID(uint32 acct_id);
Lua_Client GetClientByID(int id);
Lua_Client GetClientByCharID(uint32 char_id);
Lua_Client GetClientByWID(uint32 wid);
Lua_Object GetObjectByID(int id);
Lua_Object GetObjectByDBID(uint32 db_id);
Lua_Door GetDoorsByID(int id);
Lua_Door GetDoorsByDBID(uint32 db_id);
Lua_Door GetDoorsByDoorID(uint32 door_id);
Lua_Door FindDoor(uint32 id);
Lua_Group GetGroupByMob(Lua_Mob mob);
Lua_Group GetGroupByClient(Lua_Client client);
Lua_Group GetGroupByID(int id);
Lua_Group GetGroupByLeaderName(const char *name);
Lua_Raid GetRaidByID(int id);
Lua_Raid GetRaidByClient(Lua_Client client);
Lua_Corpse GetCorpseByOwner(Lua_Client client);
Lua_Corpse GetCorpseByID(int id);
Lua_Corpse GetCorpseByName(const char *name);
Lua_Spawn GetSpawnByID(uint32 id);
void ClearClientPetitionQueue();
bool CanAddHateForMob(Lua_Mob p);
void Message(uint32 guild_dbid, uint32 type, const char *message);
void MessageStatus(uint32 guild_dbid, int min_status, uint32 type, const char *message);
void MessageClose(Lua_Mob sender, bool skip_sender, float dist, uint32 type, const char *message);
void RemoveFromTargets(Lua_Mob mob);
void ReplaceWithTarget(Lua_Mob target, Lua_Mob new_target);
void OpenDoorsNear(Lua_NPC opener);
std::string MakeNameUnique(const char *name);
std::string RemoveNumbers(const char *name);
void SignalMobsByNPCID(uint32 npc_id, int signal);
int DeleteNPCCorpses();
int DeletePlayerCorpses();
void HalveAggro(Lua_Mob who);
void DoubleAggro(Lua_Mob who);
void ClearFeignAggro(Lua_Mob who);
bool Fighting(Lua_Mob who);
void RemoveFromHateLists(Lua_Mob who);
void RemoveFromHateLists(Lua_Mob who, bool set_to_one);
void MessageGroup(Lua_Mob who, bool skip_close, uint32 type, const char *message);
Lua_Client GetRandomClient(float x, float y, float z, float dist);
Lua_Client GetRandomClient(float x, float y, float z, float dist, Lua_Client exclude);
Lua_Mob_List GetMobList();
Lua_Client_List GetClientList();
Lua_NPC_List GetNPCList();
Lua_Corpse_List GetCorpseList();
Lua_Object_List GetObjectList();
Lua_Doors_List GetDoorsList();
Lua_Spawn_List GetSpawnList();
void SignalAllClients(int signal);
```

Lua_Mob_List, Lua_Client_List, Lua_NPC_List, Lua_Corpse_List, Lua_Object_List and Lua_Doors_List are Lua tables that have an entries field that is a table that contains the entity list of all those types.