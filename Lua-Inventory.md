Inventory is a class exported to Lua that represent the Inventory object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
inventory.null -- Returns true if this object is null
inventory.valid -- Returns true if this object is not null
```

### Member Functions
```
Inventory() -- Creates a null Inventory
ItemInst GetItem(Integer slot_id);
ItemInst GetItem(Integer slot_id, Integer bag_slot);
Integer PutItem(Integer slot_id, ItemInst item);
Integer PushCursor(ItemInst item);
Boolean SwapItem(Integer slot_a, Integer slot_b);
Boolean DeleteItem(Integer slot_id);
Boolean DeleteItem(Integer slot_id, Integer quantity);
Boolean CheckNoDrop(Integer slot_id);
ItemInst PopItem(Integer slot_id);
Integer HasItem(Integer item_id);
Integer HasItem(Integer item_id, Integer quantity);
Integer HasItem(Integer item_id, Integer quantity, Integer where);
Boolean HasSpaceForItem(Item item, Integer quantity);
Integer HasItemByUse(Integer use);
Integer HasItemByUse(Integer use, uInteger8 quantity);
Integer HasItemByUse(Integer use, uInteger8 quantity, uInteger8 where);
Integer HasItemByLoreGroup(Integer loregroup);
Integer HasItemByLoreGroup(Integer loregroup, Integer where);
Integer FindFreeSlot(Boolean for_bag, Boolean try_cursor);
Integer FindFreeSlot(Boolean for_bag, Boolean try_cursor, Integer min_size);
Integer FindFreeSlot(Boolean for_bag, Boolean try_cursor, Integer min_size, Boolean is_arrow);
Integer CalcSlotId(Integer slot_id);
Integer CalcSlotId(Integer slot_id, Integer bag_slot);
Integer CalcBagIdx(Integer slot_id);
Integer CalcSlotFromMaterial(Integer material);
Integer CalcMaterialFromSlot(Integer equipslot);
Boolean CanItemFitInContainer(Item item, Item container);
Boolean SupportsContainers(Integer slot_id);
Integer GetSlotByItemInst(ItemInst inst);
```