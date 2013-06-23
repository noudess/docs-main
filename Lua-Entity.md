Entity is a class exported to Lua that represent the Entity object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
entity.null -- Returns true if this object is null
entity.valid -- Returns true if this object is not null
```

### Member Functions
```
Entity(); -- Creates a null entity
Boolean IsClient();
Boolean IsNPC();
Boolean IsMob();
Boolean IsMerc();
Boolean IsCorpse();
Boolean IsPlayerCorpse();
Boolean IsNPCCorpse();
Boolean IsObject();
Boolean IsDoor();
Boolean IsTrap();
Boolean IsBeacon();
Integer GetID();

Client CastToClient();
NPC CastToNPC();
Mob CastToMob();
Corpse CastToCorpse();
Object CastToObject();
Door CastToDoor();
```