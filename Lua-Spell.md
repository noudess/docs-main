Lua_Spell is a class exported to Lua that represents the spdat object from EQEmu.

### Properties
```
spell.null -- Returns true if this object is null
spell.valid -- Returns true if this object is not null
```

### Member Functions
```
Spell() -- Creates a null spell
Spell(int id) -- Creates a spell with a specific id
int ID();
const char *Name();
const char *Player1();
const char *TeleportZone();
const char *YouCast();
const char *OtherCasts();
const char *CastOnYou();
const char *CastOnOther();
const char *SpellFades();
float Range();
float AoeRange();
float PushBack();
float PushUp();
uint32 CastTime();
uint32 RecoveryTime();
uint32 RecastTime();
uint32 BuffdurationFormula();
uint32 BuffDuration();
uint32 AEDuration();
int Mana();
int Base(int i);
int Base2(int i);
int Max(int i);
int Components(int i);
int ComponentCounts(int i);
int NoexpendReagent(int i);
int Formula(int i);
int GoodEffect();
int Activated();
int ResistType();
int EffectID(int i);
int TargetType();
int BaseDiff();
int Skill();
int ZoneType();
int EnvironmentType();
int TimeOfDay();
int Classes(int i);
int CastingAnim();
int SpellAffectIndex();
int DisallowSit();
int Deities(int i);
int Uninterruptable();
int ResistDiff();
int RecourseLink();
int ShortBuffBox();
int DescNum();
int EffectDescNum();
int BonusHate();
int EndurCost();
int EndurTimerIndex();
int HateAdded();
int EndurUpkeep();
int NumHits();
int PVPResistBase();
int PVPResistCalc();
int PVPResistCap();
int SpellCategory();
int CanMGB();
int DispelFlag();
int MinResist();
int MaxResist();
int ViralTargets();
int ViralTimer();
int NimbusEffect();
float DirectionalStart();
float DirectionalEnd();
int SpellGroup();
int PowerfulFlag();
int CastRestriction();
bool AllowRest();
int DamageShieldType();
```