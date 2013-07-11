Door is a class exported to Lua that represent the Door object from EQEmu. All Door are also [Entity](Lua-Entity).

[Return to the Lua API](Lua-API)

### Properties
```
door.null -- Returns true if this object is null
door.valid -- Returns true if this object is not null
```

### Member Functions
```
Door() -- Creates a null Door
Void SetDoorName(String name);
String GetDoorName();
Real GetX();
Real GetY();
Real GetZ();
Real GetHeading();
Void SetX(Real x);
Void SetY(Real y);
Void SetZ(Real z);
Void SetHeading(Real h);
Void SetLocation(Real x, Real y, Real z);
Integer GetDoorDBID();
Integer GetDoorID();
Void SetSize(Integer sz);
Integer GetSize();
Void SetIncline(Integer incline);
Integer GetIncline();
Void SetOpenType(Integer type);
Integer GetOpenType();
Void SetLockPick(Integer pick);
Integer GetLockPick();
Void SetKeyItem(Integer key);
Integer GetKeyItem();
Void SetNoKeyring(Integer type);
Integer GetNoKeyring();
Void CreateDatabaseEntry();
Void ForceOpen(Mob sender);
Void ForceOpen(Mob sender, bool alt_mode);
Void ForceClose(Mob sender);
Void ForceClose(Mob sender, bool alt_mode);
```