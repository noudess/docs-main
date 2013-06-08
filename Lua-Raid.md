Lua_Raid is a class exported to Lua that represent the Raid object from EQEmu.

### Properties
```
raid.null -- Returns true if this object is null
raid.valid -- Returns true if this object is not null
```

### Member Functions
```
Raid() -- Creates a null Raid
bool IsRaidMember(const char *name);
void CastGroupSpell(Lua_Mob caster, int spell_id, uint32 group_id);
int GroupCount(uint32 group_id);
int RaidCount();
uint32 GetGroup(const char *c);
uint32 GetGroup(Lua_Client c);
void SplitExp(uint32 exp, Lua_Mob other);
uint32 GetTotalRaidDamage(Lua_Mob other);
void SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum);
void SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, Lua_Client splitter);
void BalanceHP(int penalty, uint32 group_id);
bool IsLeader(const char *c);
bool IsLeader(Lua_Client c);
bool IsGroupLeader(const char *name);
int GetHighestLevel();
int GetLowestLevel();
Lua_Client GetClientByIndex(int index);
void TeleportGroup(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h, uint32 group_id);
void TeleportRaid(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h);
int GetID();
Lua_Client GetMember(int index);
```