Lua_Group is a class exported to Lua that represent the Group object from EQEmu.

### Properties
```
group.null -- Returns true if this object is null
group.valid -- Returns true if this object is not null
```

### Member Functions
```
void DisbandGroup();
bool IsGroupMember(Lua_Mob mob);
void CastGroupSpell(Lua_Mob caster, int spell_id);
void SplitExp(uint32 exp, Lua_Mob other);
void GroupMessage(Lua_Mob sender, int language, const char *message);
uint32 GetTotalGroupDamage(Lua_Mob other);
void SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum);
void SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, Lua_Client splitter);
void SetLeader(Lua_Mob leader);
Lua_Mob GetLeader();
const char *GetLeaderName();
bool IsLeader(Lua_Mob leader);
int GroupCount();
int GetHighestLevel();
void TeleportGroup(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h);
int GetID();
Lua_Mob GetMember(int index);
```