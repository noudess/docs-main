Lua_Entity is a class exported to Lua that represent the Entity object from EQEmu.

### Properties
```
entity.null - Returns true if this object is null
entity.valid - Returns true if this object is not null
```

### Member Functions
```
Entity() - Creates a null entity
bool IsClient()
bool IsNPC()
bool IsMob()
bool IsMerc()
bool IsCorpse()
bool IsPlayerCorpse()
bool IsNPCCorpse()
bool IsObject()
bool IsDoor()
bool IsTrap()
bool IsBeacon()
int GetID()
Lua_Client CastToClient()
Lua_NPC CastToNPC()
Lua_Mob CastToMob()
Lua_Corpse CastToCorpse()
Lua_Object CastToObject()
Lua_Door CastToDoor()
```