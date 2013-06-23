Corpse is a class exported to Lua that represent the Corpse object from EQEmu. All Corpse are also [Mob](Lua-Mob).

[Return to the Lua API](Lua-API)

### Properties
```
corpse.null -- Returns true if this object is null
corpse.valid -- Returns true if this object is not null
```

### Member Functions
```
Corpse() -- Creates a null Corpse
Integer GetCharID();
Integer GetDecayTime();
Void Lock();
Void UnLock();
Boolean IsLocked();
Void ResetLooter();
Integer GetDBID();
Boolean IsRezzed();
String GetOwnerName();
Boolean Save();
Void Delete();
Void Bury();
Void Depop();
Integer CountItems();
Void AddItem(Integer itemnum, uInteger charges, Integer slot, Integer aug1, Integer aug2, Integer aug3, Integer aug4, Integer aug5);
Integer GetWornItem(Integer equipSlot);
Void RemoveItem(Integer lootslot);
Void SetCash(Integer copper, Integer silver, Integer gold, Integer platinum);
Void RemoveCash();
Boolean IsEmpty();
Void SetDecayTimer(Integer decaytime);
Boolean CanMobLoot(Integer charid);
Void AllowMobLoot(Mob them, uInteger8 slot);
Boolean Summon(Client client, Boolean spell, Boolean checkdistance);
Integer GetCopper();
Integer GetSilver();
Integer GetGold();
Integer GetPlatinum();
Void AddLooter(Mob who);
```