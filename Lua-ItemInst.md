ItemInst is a class exported to Lua that represent the ItemInst object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
item.null -- Returns true if this object is null
item.valid -- Returns true if this object is not null
```

### Member Functions
```
ItemInst() -- Creates a null ItemInst
ItemInst(Integer item_id) -- Creates a new ItemInst of item_id
ItemInst(Integer item_id, Integer charges) -- Creates a new ItemInst of item_id with charges
Boolean IsType(Integer item_class);
Boolean IsStackable();
Boolean IsEquipable(Integer race, Integer class_);
Boolean IsEquipable(Integer slot_id);
Boolean IsAugmentable();
Integer GetAugmentType();
Boolean IsExpendable();
ItemInst GetItem(Integer slot);
Item GetItem();
Void SetItem(Item item);
Item GetUnscaledItem(Integer slot);
Integer GetItemID(Integer slot);
Integer GetTotalItemCount();
ItemInst GetAugment(Integer slot);
Integer GetAugmentItemID(Integer slot);
Boolean IsAugmented();
Boolean IsWeapon();
Boolean IsAmmo();
Integer GetID();
Integer GetItemScriptID();
Integer GetCharges();
Void SetCharges(Integer charges);
Integer GetPrice();
Void SetPrice(Integer price);
Void SetColor(Integer color);
Integer GetColor();
Boolean IsInstNoDrop();
Void SetInstNoDrop(Boolean flag);
String GetCustomDataString();
Void SetCustomData(String identifier, String value);
Void SetCustomData(String identifier, Integer value);
Void SetCustomData(String identifier, Real value);
Void SetCustomData(String identifier, Boolean value);
String GetCustomData(String identifier);
Void DeleteCustomData(String identifier);
Void SetScaling(Boolean val);
Void SetScale(Real scale_factor);
Integer GetExp();
Void SetExp(Integer exp);
Void AddExp(Integer exp);
Integer GetMaxEvolveLvl();
Integer GetKillsNeeded(Integer current_level);
ItemInst Clone();
```