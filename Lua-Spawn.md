Spawn is a class exported to Lua that represents the spawn2 object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
spawn.null -- Returns true if this object is null
spawn.valid -- Returns true if this object is not null
```

### Member Functions
```
Spawn() -- Creates a null spawn
Void LoadGrid();
Void Enable();
Void Disable();
Boolean Enabled();
Void Reset();
Void Depop();
Void Repop();
Void Repop(Integer delay);
Void ForceDespawn();
Integer GetID();
Real GetX();
Real GetY();
Real GetZ();
Real GetHeading();
Void SetRespawnTimer(Integer newrespawntime);
Void SetVariance(Integer newvariance);
Integer GetVariance();
Integer RespawnTimer();
Integer SpawnGroupID();
Integer CurrentNPCID();
Void SetCurrentNPCID(Integer nid);
Integer GetSpawnCondition();
Boolean NPCPointerValid();
Void SetNPCPointer(NPC n);
Void SetTimer(Integer duration);
Integer GetKillCount();
```