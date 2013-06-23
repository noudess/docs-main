Raid is a class exported to Lua that represent the Raid object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
raid.null -- Returns true if this object is null
raid.valid -- Returns true if this object is not null
```

### Member Functions
```
Raid() -- Creates a null Raid
Boolean IsRaidMember(String name);
Void CastGroupSpell(Mob caster, Integer spell_id, Integer group_id);
Integer GroupCount(Integer group_id);
Integer RaidCount();
Integer GetGroup(String c);
Integer GetGroup(Client c);
Void SplitExp(Integer exp, Mob other);
Integer GetTotalRaidDamage(Mob other);
Void SplitMoney(Integer copper, Integer silver, Integer gold, Integer platinum);
Void SplitMoney(Integer copper, Integer silver, Integer gold, Integer platinum, Client splitter);
Void BalanceHP(Integer penalty, Integer group_id);
Boolean IsLeader(String c);
Boolean IsLeader(Client c);
Boolean IsGroupLeader(String name);
Integer GetHighestLevel();
Integer GetLowestLevel();
Client GetClientByIndex(Integer index);
Void TeleportGroup(Mob sender, Integer zone_id, Integer instance_id, Real x, Real y, Real z, Real h, Integer group_id);
Void TeleportRaid(Mob sender, Integer zone_id, Integer instance_id, Real x, Real y, Real z, Real h);
Integer GetID();
Client GetMember(Integer index);
```