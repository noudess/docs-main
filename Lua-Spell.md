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
int GetID();
const char *GetName();
const char *GetPlayer1();
const char *GetTeleportZone();
const char *GetYouCast();
const char *GetOtherCasts();
const char *GetCastOnYou();
const char *GetCastOnOther();
const char *GetSpellFades();
float GetRange();
float GetAoeRange();
float GetPushBack();
float GetPushUp();
uint32 GetCastTime();
uint32 GetRecoveryTime();
uint32 GetRecastTime();
uint32 GetBuffdurationFormula();
uint32 GetBuffDuration();
uint32 GetAEDuration();
int GetMana();
int GetBase(int i);
int GetBase2(int i);
int GetMax(int i);
int GetComponents(int i);
int GetComponentCounts(int i);
int GetNoexpendReagent(int i);
int GetFormula(int i);
int GetGoodEffect();
int GetActivated();
int GetResistType();
int GetEffectID(int i);
int GetTargetType();
int GetBaseDiff();
int GetSkill();
int GetZoneType();
int GetEnvironmentType();
int GetTimeOfDay();
int GetClasses(int i);
int GetCastingAnim();
int GetSpellAffectIndex();
int GetDisallowSit();
int GetDeities(int i);
int GetUninterruptable();
int GetResistDiff();
int GetRecourseLink();
int GetShortBuffBox();
int GetDescNum();
int GetEffectDescNum();
int GetBonusHate();
int GetEndurCost();
int GetEndurTimerIndex();
int GetHateAdded();
int GetEndurUpkeep();
int GetNumHits();
int GetPVPResistBase();
int GetPVPResistCalc();
int GetPVPResistCap();
int GetSpellCategory();
int GetCanMGB();
int GetDispelFlag();
int GetMinResist();
int GetMaxResist();
int GetViralTargets();
int GetViralTimer();
int GetNimbusEffect();
float GetDirectionalStart();
float GetDirectionalEnd();
int GetSpellGroup();
int GetPowerfulFlag();
int GetCastRestriction();
bool GetAllowRest();
int GetDamageShieldType();
```