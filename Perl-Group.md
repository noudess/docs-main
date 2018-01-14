Group is a class exported to Perl that represent the Group object from EQEmu.

### Properties
```
group.null -- Returns true if this object is null
group.valid -- Returns true if this object is not null
```

### Member Functions
```
void Group::DisbandGroup()
void Group::IsGroupMember( client)
void Group::CastGroupSpell( caster,  spellid)
void Group::SplitExp( exp,  other)
void Group::GroupMessage( sender,  language, string message)
void Group::GetTotalGroupDamage( other)
void Group::SplitMoney(int copper, int silver, int gold, int platinum)
void Group::SetLeader( newleader)
void Group::GetLeader()
void Group::GetLeaderName()
void Group::SendHPPacketsTo( newmember)
void Group::SendHPPacketsFrom( newmember)
void Group::IsLeader( leadertest)
void Group::GroupCount()
void Group::GetHighestLevel()
void Group::TeleportGroup( sender,  zoneID, float x, float y, float z, float heading)
void Group::GetID()
void Group::GetMember( index)

```