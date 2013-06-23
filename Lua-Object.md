Lua_Object is a class exported to Lua that represent the Object object from EQEmu. All Lua_Object are also [Lua_Entity](Lua-Entity).

[Return to the Lua API](Lua-API)

### Properties
```
object.null -- Returns true if this object is null
object.valid -- Returns true if this object is not null
```

### Member Functions
```
Object() -- Creates a null Object
void Depop();
void Repop();
void SetModelName(const char *name);
const char *GetModelName();
float GetX();
float GetY();
float GetZ();
float GetHeading();
void SetX(float x);
void SetY(float y);
void SetZ(float z);
void SetHeading(float h);
void SetLocation(float x, float y, float z);
void SetItemID(uint32 item_id);
uint32 GetItemID();
void SetIcon(uint32 icon);
uint32 GetIcon();
void SetType(uint32 type);
uint32 GetType();
uint32 GetDBID();
void ClearUser();
void SetID(int user);
int GetID();
bool Save();
uint32 VarSave();
void DeleteItem(int index);
void StartDecay();
void Delete();
void Delete(bool reset_state);
bool IsGroundSpawn();
void Close();
const char *GetEntityVariable(const char *name);
void SetEntityVariable(const char *name, const char *value);
bool EntityVariableExists(const char *name);
```