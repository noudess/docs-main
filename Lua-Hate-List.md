Lua_HateEntry is a class exported to Lua that represent the HateEntry object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
hate.null -- Returns true if this object is null
hate.valid -- Returns true if this object is not null
```

### Member Functions
```
Lua_Mob GetEnt();
void SetEnt(Lua_Mob e);
int GetDamage();
void SetDamage(int value);
int GetHate();
void SetHate(int value);
int GetFrenzy();
void SetFrenzy(bool value);
```

Lua_HateList is a table exported to Lua that contains a field 'entries' that contains hate entries of the hate list.