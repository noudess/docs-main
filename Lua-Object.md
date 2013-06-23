Object is a class exported to Lua that represent the Object object from EQEmu. All Object are also [Entity](Lua-Entity).

[Return to the Lua API](Lua-API)

### Properties
```
object.null -- Returns true if this object is null
object.valid -- Returns true if this object is not null
```

### Member Functions
```
Object() -- Creates a null Object
Void Depop();
Void Repop();
Void SetModelName(String name);
String GetModelName();
Real GetX();
Real GetY();
Real GetZ();
Real GetHeading();
Void SetX(Real x);
Void SetY(Real y);
Void SetZ(Real z);
Void SetHeading(Real h);
Void SetLocation(Real x, Real y, Real z);
Void SetItemID(Integer item_id);
Integer GetItemID();
Void SetIcon(Integer icon);
Integer GetIcon();
Void SetType(Integer type);
Integer GetType();
Integer GetDBID();
Void ClearUser();
Void SetID(Integer user);
Integer GetID();
Boolean Save();
Integer VarSave();
Void DeleteItem(Integer index);
Void StartDecay();
Void Delete();
Void Delete(Boolean reset_state);
Boolean IsGroundSpawn();
Void Close();
String GetEntityVariable(String name);
Void SetEntityVariable(String name, String value);
Boolean EntityVariableExists(String name);
```