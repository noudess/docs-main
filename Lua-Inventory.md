Lua_Inventory is a class exported to Lua that represent the Inventory object from EQEmu.

### Properties
```
inventory.null -- Returns true if this object is null
inventory.valid -- Returns true if this object is not null
```

### Member Functions
```
Inventory() -- Creates a null Inventory
Lua_ItemInst GetItem(int slot_id);
Lua_ItemInst GetItem(int slot_id, int bag_slot);
int PutItem(int slot_id, Lua_ItemInst item);
int PushCursor(Lua_ItemInst item);
bool SwapItem(int slot_a, int slot_b);
bool DeleteItem(int slot_id);
bool DeleteItem(int slot_id, int quantity);
bool CheckNoDrop(int slot_id);
Lua_ItemInst PopItem(int slot_id);
int HasItem(int item_id);
int HasItem(int item_id, int quantity);
int HasItem(int item_id, int quantity, int where);
bool HasSpaceForItem(Lua_Item item, int quantity);
int HasItemByUse(int use);
int HasItemByUse(int use, uint8 quantity);
int HasItemByUse(int use, uint8 quantity, uint8 where);
int HasItemByLoreGroup(uint32 loregroup);
int HasItemByLoreGroup(uint32 loregroup, int where);
int FindFreeSlot(bool for_bag, bool try_cursor);
int FindFreeSlot(bool for_bag, bool try_cursor, int min_size);
int FindFreeSlot(bool for_bag, bool try_cursor, int min_size, bool is_arrow);
int CalcSlotId(int slot_id);
int CalcSlotId(int slot_id, int bag_slot);
int CalcBagIdx(int slot_id);
int CalcSlotFromMaterial(int material);
int CalcMaterialFromSlot(int equipslot);
bool CanItemFitInContainer(Lua_Item item, Lua_Item container);
bool SupportsContainers(int slot_id);
int GetSlotByItemInst(Lua_ItemInst inst);
```