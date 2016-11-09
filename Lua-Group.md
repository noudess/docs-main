Group is a class exported to Lua that represent the Group object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
group.null -- Returns true if this object is null
group.valid -- Returns true if this object is not null
```

### Member Functions
```
Group() -- Creates a null Group
Void DisbandGroup();
Boolean IsGroupMember(Mob mob);
Void CastGroupSpell(Mob caster, Integer spell_id);
Void SplitExp(Integer exp, Mob other);
Void GroupMessage(Mob sender, Integer language, String message);
Integer GetTotalGroupDamage(Mob other);
Void SplitMoney(Integer copper, Integer silver, Integer gold, Integer platinum);
Void SplitMoney(Integer copper, Integer silver, Integer gold, Integer platinum, Client splitter);
Void SetLeader(Mob leader);
Mob GetLeader();
String GetLeaderName();
Boolean IsLeader(Mob leader);
Integer GroupCount();
Integer GetHighestLevel();
Integer GetLowestLevel();
Void TeleportGroup(Mob sender, Integer zone_id, Integer instance_id, Real x, Real y, Real z, Real h);
Integer GetID();
Mob GetMember(Integer index);
```