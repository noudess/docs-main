Lua_Corpse is a class exported to Lua that represent the Corpse object from EQEmu. All Lua_Corpse are also [Lua_Mob](Lua-Mob).

### Properties
```
corpse.null -- Returns true if this object is null
corpse.valid -- Returns true if this object is not null
```

### Member Functions
```
Corpse() -- Creates a null Corpse
uint32 GetCharID();
uint32 GetDecayTime();
void Lock();
void UnLock();
bool IsLocked();
void ResetLooter();
uint32 GetDBID();
bool IsRezzed();
const char *GetOwnerName();
bool Save();
void Delete();
void Bury();
void Depop();
uint32 CountItems();
void AddItem(uint32 itemnum, uint16 charges, int16 slot, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5);
uint32 GetWornItem(int16 equipSlot);
void RemoveItem(uint16 lootslot);
void SetCash(uint32 copper, uint32 silver, uint32 gold, uint32 platinum);
void RemoveCash();
bool IsEmpty();
void SetDecayTimer(uint32 decaytime);
bool CanMobLoot(int charid);
void AllowMobLoot(Lua_Mob them, uint8 slot);
bool Summon(Lua_Client client, bool spell, bool checkdistance);
uint32 GetCopper();
uint32 GetSilver();
uint32 GetGold();
uint32 GetPlatinum();
void AddLooter(Lua_Mob who);
```