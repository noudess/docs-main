Lua_Door is a class exported to Lua that represent the Door object from EQEmu. All Lua_Door are also [Lua_Entity](Lua-Entity).

### Properties
```
door.null -- Returns true if this object is null
door.valid -- Returns true if this object is not null
```

### Member Functions
```
Door() -- Creates a null Door
void SetDoorName(const char *name);
const char *GetDoorName();
float GetX();
float GetY();
float GetZ();
float GetHeading();
void SetX(float x);
void SetY(float y);
void SetZ(float z);
void SetHeading(float h);
void SetLocation(float x, float y, float z);
uint32 GetDoorDBID();
uint32 GetDoorID();
void SetSize(uint32 sz);
uint32 GetSize();
void SetIncline(uint32 incline);
uint32 GetIncline();
void SetOpenType(uint32 type);
uint32 GetOpenType();
void SetLockPick(uint32 pick);
uint32 GetLockPick();
void SetKeyItem(uint32 key);
uint32 GetKeyItem();
void SetNoKeyring(int type);
int GetNoKeyring();
void CreateDatabaseEntry();
```