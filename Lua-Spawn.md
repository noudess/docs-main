Lua_Spawn is a class exported to Lua that represents the spawn2 object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
spawn.null -- Returns true if this object is null
spawn.valid -- Returns true if this object is not null
```

### Member Functions
```
Spawn() -- Creates a null spawn
void LoadGrid();
void Enable();
void Disable();
bool Enabled();
void Reset();
void Depop();
void Repop();
void Repop(uint32 delay);
void ForceDespawn();
uint32 GetID();
float GetX();
float GetY();
float GetZ();
float GetHeading();
void SetRespawnTimer(uint32 newrespawntime);
void SetVariance(uint32 newvariance);
uint32 GetVariance();
uint32 RespawnTimer();
uint32 SpawnGroupID();
uint32 CurrentNPCID();
void SetCurrentNPCID(uint32 nid);
uint32 GetSpawnCondition();
bool NPCPointerValid();
void SetNPCPointer(Lua_NPC n);
void SetTimer(uint32 duration);
uint32 GetKillCount();
```