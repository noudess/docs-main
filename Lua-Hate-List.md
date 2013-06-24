HateEntry is a class exported to Lua that represent the HateEntry object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
hate.null -- Returns true if this object is null
hate.valid -- Returns true if this object is not null
```

### Member Functions
```
Mob GetEnt();
Void SetEnt(Mob e);
Integer GetDamage();
Void SetDamage(Integer value);
Integer GetHate();
Void SetHate(Integer value);
Integer GetFrenzy();
Void SetFrenzy(Boolean value);
```

HateList is a table exported to Lua that contains a field 'entries' that contains hate entries of the hate list.