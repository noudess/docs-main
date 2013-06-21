Lua_ItemInst is a class exported to Lua that represent the ItemInst object from EQEmu.

### Properties
```
item.null -- Returns true if this object is null
item.valid -- Returns true if this object is not null
```

### Member Functions
```
ItemInst() -- Creates a null ItemInst
ItemInst(int item_id) -- Creates a new ItemInst of item_id
ItemInst(int item_id, int charges) -- Creates a new ItemInst of item_id with charges
bool IsType(int item_class);
bool IsStackable();
bool IsEquipable(int race, int class_);
bool IsEquipable(int slot_id);
bool IsAugmentable();
int GetAugmentType();
bool IsExpendable();
Lua_ItemInst GetItem(int slot);
Lua_Item GetItem();
void SetItem(Lua_Item item);
Lua_Item GetUnscaledItem(int slot);
uint32 GetItemID(int slot);
int GetTotalItemCount();
Lua_ItemInst GetAugment(int slot);
uint32 GetAugmentItemID(int slot);
bool IsAugmented();
bool IsWeapon();
bool IsAmmo();
uint32 GetID();
uint32 GetItemScriptID();
int GetCharges();
void SetCharges(int charges);
uint32 GetPrice();
void SetPrice(uint32 price);
void SetColor(uint32 color);
uint32 GetColor();
bool IsInstNoDrop();
void SetInstNoDrop(bool flag);
std::string GetCustomDataString();
void SetCustomData(std::string identifier, std::string value);
void SetCustomData(std::string identifier, int value);
void SetCustomData(std::string identifier, float value);
void SetCustomData(std::string identifier, bool value);
std::string GetCustomData(std::string identifier);
void DeleteCustomData(std::string identifier);
void SetScaling(bool val);
void SetScale(double scale_factor);
uint32 GetExp();
void SetExp(uint32 exp);
void AddExp(uint32 exp);
int GetMaxEvolveLvl();
uint32 GetKillsNeeded(int current_level);
Lua_ItemInst Clone();
```