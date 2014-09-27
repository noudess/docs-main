Spell is a class exported to Lua that represents the spdat object from EQEmu.

[Return to the Lua API](Lua-API)

### Properties
```
spell.null -- Returns true if this object is null
spell.valid -- Returns true if this object is not null
```

### Member Functions
```
Spell() -- Creates a null spell
Spell(Integer id) -- Creates a spell with a specific id
Integer ID();
String Name();
String Player1();
String TeleportZone();
String YouCast();
String OtherCasts();
String CastOnYou();
String CastOnOther();
String SpellFades();
Real Range();
Real AoeRange();
Real PushBack();
Real PushUp();
Integer CastTime();
Integer RecoveryTime();
Integer RecastTime();
Integer BuffdurationFormula();
Integer BuffDuration();
Integer AEDuration();
Integer Mana();
Integer Base(Integer i);
Integer Base2(Integer i);
Integer Max(Integer i);
Integer Components(Integer i);
Integer ComponentCounts(Integer i);
Integer NoexpendReagent(Integer i);
Integer Formula(Integer i);
Integer GoodEffect();
Integer Activated();
Integer ResistType();
Integer EffectID(Integer i);
Integer TargetType();
Integer BaseDiff();
Integer Skill();
Integer ZoneType();
Integer EnvironmentType();
Integer TimeOfDay();
Integer Classes(Integer i);
Integer CastingAnim();
Integer SpellAffectIndex();
Integer DisallowSit();
Integer Deities(Integer i);
Integer Uninterruptable();
Integer ResistDiff();
Integer RecourseLink();
Integer ShortBuffBox();
Integer DescNum();
Integer EffectDescNum();
Integer BonusHate();
Integer EndurCost();
Integer EndurTimerIndex();
Integer HateAdded();
Integer EndurUpkeep();
Integer NumHits();
Integer PVPResistBase();
Integer PVPResistCalc();
Integer PVPResistCap();
Integer SpellCategory();
Integer CanMGB();
Integer DispelFlag();
Integer MinResist();
Integer MaxResist();
Integer ViralTargets();
Integer ViralTimer();
Integer NimbusEffect();
Real DirectionalStart();
Real DirectionalEnd();
Integer SpellGroup();
Integer PowerfulFlag();
Integer CastRestriction();
Boolean AllowRest();
Boolean InCombat();
Boolean OutOfCombat();
Integer AEMaxTargets();
Integer MaxTargets();
Boolean PersistDeath();
Real MinDist();
Real MinDistMod();
Real MaxDist();
Real MaxDistMod();
Real MinRange();
Integer DamageShieldType();
```