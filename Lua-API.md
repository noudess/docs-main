[Return to the Lua Parser](Lua-Parser)

The Lua API consisted of many exported classes and some general functions.
* [Client](Lua-Client)
* [Corpse](Lua-Corpse)
* [Door](Lua-Door)
* [Entity](Lua-Entity)
* [EntityList](Lua-Entity-List)
* [Group](Lua-Group)
* [HateList](Lua-Hate-List)
* [Inventory](Lua-Inventory)
* [Item](Lua-Item)
* [ItemInst](Lua-ItemInst)
* [Mob](Lua-Mob)
* [NPC](Lua-NPC)
* [Object](Lua-Object)
* [Packet](Lua-Packet)
* [Raid](Lua-Raid)
* [Spell](Lua-Spell)
* [Spawn](Lua-Spawn)
* [Lua General Functions](Lua-General-Functions)
* [Lua Constants](Lua-Constants)

# Packet
```lua
packet:GetOpcode(); -- int
packet:GetRawOpcode(); -- int
packet:GetSize(); -- int
packet:Lua_Packet(const Lua_Packet& o); -- Lua_Packet::Lua_Packet(const
packet:ReadDouble(int offset); -- double
packet:ReadFixedLengthString(int offset, int string_length); -- std::string
packet:ReadFloat(int offset); -- float
packet:ReadInt16(int offset); -- int
packet:ReadInt32(int offset); -- int
packet:ReadInt64(int offset); -- int64
packet:ReadInt8(int offset); -- int
packet:ReadString(int offset); -- std::string
packet:SetOpcode(int op); -- void
packet:SetRawOpcode(int op); -- void
packet:WriteDouble(int offset, double value); -- void
packet:WriteFixedLengthString(int offset, std::string value, int string_length); -- void
packet:WriteFloat(int offset, float value); -- void
packet:WriteInt16(int offset, int value); -- void
packet:WriteInt32(int offset, int value); -- void
packet:WriteInt64(int offset, int64 value); -- void
packet:WriteInt8(int offset, int value); -- void
packet:WriteString(int offset, std::string value); -- void
packet:operator=(const Lua_Packet& o); -- Lua_Packet&
```

# Group
```lua
group:CastGroupSpell(Lua_Mob caster, int spell_id); -- void
group:DisbandGroup(); -- void
group:GetHighestLevel(); -- int
group:GetID(); -- int
group:GetLeader(); -- Lua_Mob
group:GetLowestLevel(); -- int
group:GetMember(int index); -- Lua_Mob
group:GetTotalGroupDamage(Lua_Mob other); -- uint32
group:GroupCount(); -- int
group:GroupMessage(Lua_Mob sender, int language, const char *message); -- void
group:IsGroupMember(Lua_Mob mob); -- bool
group:IsLeader(Lua_Mob leader); -- bool
group:SetLeader(Lua_Mob leader); -- void
group:SplitExp(uint32 exp, Lua_Mob other); -- void
group:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
group:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, Lua_Client splitter); -- void
group:TeleportGroup(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h); -- void
```

# Mob
```lua
mob:AddNimbusEffect(int effect_id); -- void
mob:AddToHateList(Lua_Mob other); -- void
mob:AddToHateList(Lua_Mob other, int hate); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage, bool yell_for_help); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage, bool yell_for_help, bool frenzy); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage, bool yell_for_help, bool frenzy, bool buff_tic); -- void
mob:Attack(Lua_Mob other); -- bool
mob:Attack(Lua_Mob other, int hand); -- bool
mob:Attack(Lua_Mob other, int hand, bool from_riposte); -- bool
mob:Attack(Lua_Mob other, int hand, bool from_riposte, bool is_strikethrough); -- bool
mob:Attack(Lua_Mob other, int hand, bool from_riposte, bool is_strikethrough, bool is_from_spell); -- bool
mob:AttackAnimation(int Hand, Lua_ItemInst weapon); -- int
mob:BehindMob(); -- bool
mob:BehindMob(Lua_Mob other); -- bool
mob:BehindMob(Lua_Mob other, float x); -- bool
mob:BehindMob(Lua_Mob other, float x, float y); -- bool
mob:BuffFadeAll(); -- void
mob:BuffFadeByEffect(int effect_id); -- void
mob:BuffFadeByEffect(int effect_id, int skipslot); -- void
mob:BuffFadeBySlot(int slot); -- void
mob:BuffFadeBySlot(int slot, bool recalc_bonuses); -- void
mob:BuffFadeBySpellID(int spell_id); -- void
mob:CalculateDistance(double x, double y, double z); -- float
mob:CalculateHeadingToTarget(double in_x, double in_y); -- double
mob:CalculateNewPosition(double x, double y, double z, double speed); -- bool
mob:CalculateNewPosition(double x, double y, double z, double speed, bool check_z); -- bool
mob:CameraEffect(uint32 duration, uint32 intensity); -- void
mob:CameraEffect(uint32 duration, uint32 intensity, Lua_Client c); -- void
mob:CameraEffect(uint32 duration, uint32 intensity, Lua_Client c, bool global); -- void
mob:CanBuffStack(int spell_id, int caster_level); -- int
mob:CanBuffStack(int spell_id, int caster_level, bool fail_if_overwrite); -- int
mob:CanThisClassBlock(); -- bool
mob:CanThisClassDodge(); -- bool
mob:CanThisClassDoubleAttack(); -- bool
mob:CanThisClassDualWield(); -- bool
mob:CanThisClassParry(); -- bool
mob:CanThisClassRiposte(); -- bool
mob:CastSpell(int spell_id, int target_id); -- bool
mob:CastSpell(int spell_id, int target_id, int slot); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost, int item_slot); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost, int item_slot, int timer,; -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost, int item_slot, int timer,; -- bool
mob:ChangeBeard(int in); -- void
mob:ChangeBeardColor(int in); -- void
mob:ChangeDrakkinDetails(int in); -- void
mob:ChangeDrakkinHeritage(int in); -- void
mob:ChangeDrakkinTattoo(int in); -- void
mob:ChangeEyeColor1(int in); -- void
mob:ChangeEyeColor2(int in); -- void
mob:ChangeGender(int in); -- void
mob:ChangeHairColor(int in); -- void
mob:ChangeHairStyle(int in); -- void
mob:ChangeHelmTexture(int in); -- void
mob:ChangeLuclinFace(int in); -- void
mob:ChangeRace(int in); -- void
mob:ChangeSize(double in_size); -- void
mob:ChangeSize(double in_size, bool no_restriction); -- void
mob:ChangeTexture(int in); -- void
mob:Charmed(); -- bool
mob:CheckAggro(Lua_Mob other); -- bool
mob:CheckAggroAmount(int spell_id); -- int
mob:CheckAggroAmount(int spell_id, bool is_proc); -- int
mob:CheckHealAggroAmount(int spell_id); -- int
mob:CheckHealAggroAmount(int spell_id, uint32 heal_possible); -- int
mob:CheckLoS(Lua_Mob other); -- bool
mob:CheckLoSToLoc(double x, double y, double z); -- bool
mob:CheckLoSToLoc(double x, double y, double z, double mob_size); -- bool
mob:CheckNumHitsRemaining(int type, int32 buff_slot, uint16 spell_id); -- void
mob:ClearSpecialAbilities(); -- void
mob:CombatRange(Lua_Mob other); -- bool
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill); -- void
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill, bool avoidable); -- void
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill, bool avoidable, int buffslot); -- void
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill, bool avoidable, int buffslot, bool buff_tic); -- void
mob:DelGlobal(const char *varname); -- void
mob:Depop(); -- void
mob:Depop(bool start_spawn_timer); -- void
mob:DivineAura(); -- bool
mob:DoAnim(int anim_num); -- void
mob:DoAnim(int anim_num, int type); -- void
mob:DoAnim(int anim_num, int type, bool ackreq); -- void
mob:DoAnim(int anim_num, int type, bool ackreq, int filter); -- void
mob:DoArcheryAttackDmg(Lua_Mob other); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo, int weapon_damage); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo, int weapon_damage, int chance_mod); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo, int weapon_damage, int chance_mod,; -- void
mob:DoKnockback(Lua_Mob caster, uint32 pushback, uint32 pushup); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill, int chance_mod); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill, int chance_mod, int focus); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill, int chance_mod, int focus, bool can_riposte); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage, int min_damage); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage, int min_damage, int hate_override); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage, int min_damage, int hate_override, int reuse_time); -- void
mob:DoThrowingAttackDmg(Lua_Mob other); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item, int weapon_damage); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item, int weapon_damage, int chance_mod); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item, int weapon_damage, int chance_mod,; -- void
mob:DoubleAggro(Lua_Mob other); -- void
mob:Emote(const char *message); -- void
mob:EntityVariableExists(const char *name); -- bool
mob:FaceTarget(Lua_Mob target); -- void
mob:FindBuff(int spell_id); -- bool
mob:FindGroundZ(double x, double y); -- double
mob:FindGroundZ(double x, double y, double z); -- double
mob:FindType(int type); -- bool
mob:FindType(int type, bool offensive); -- bool
mob:FindType(int type, bool offensive, int threshold); -- bool
mob:GMMove(double x, double y, double z); -- void
mob:GMMove(double x, double y, double z, double heading); -- void
mob:GMMove(double x, double y, double z, double heading, bool send_update); -- void
mob:Gate(); -- void
mob:GetAA(int id); -- int
mob:GetAABonuses(); -- Lua_StatBonuses
mob:GetAAByAAID(int id); -- int
mob:GetAC(); -- int
mob:GetAGI(); -- int
mob:GetATK(); -- int
mob:GetAggroRange(); -- float
mob:GetAllowBeneficial(); -- bool
mob:GetAppearance(); -- uint32
mob:GetAssistRange(); -- float
mob:GetBaseGender(); -- int
mob:GetBaseRace(); -- int
mob:GetBaseSize(); -- float
mob:GetBeard(); -- int
mob:GetBeardColor(); -- int
mob:GetBodyType(); -- int
mob:GetBuffSlotFromType(int slot); -- int
mob:GetCHA(); -- int
mob:GetCR(); -- int
mob:GetCasterLevel(int spell_id); -- int
mob:GetClass(); -- int
mob:GetCorruption(); -- int
mob:GetDEX(); -- int
mob:GetDR(); -- int
mob:GetDamageAmount(Lua_Mob target); -- uint32
mob:GetDeity(); -- int
mob:GetDrakkinDetails(); -- int
mob:GetDrakkinHeritage(); -- int
mob:GetDrakkinTattoo(); -- int
mob:GetEyeColor1(); -- int
mob:GetEyeColor2(); -- int
mob:GetFR(); -- int
mob:GetFcDamageAmtIncoming(Lua_Mob caster, uint32 spell_id, bool use_skill, uint16 skill); -- int
mob:GetFlurryChance(); -- int
mob:GetGender(); -- int
mob:GetGlobal(const char *varname); -- std::string
mob:GetHP(); -- int
mob:GetHPRatio(); -- double
mob:GetHairColor(); -- int
mob:GetHairStyle(); -- int
mob:GetHandToHandDamage(); -- int
mob:GetHandToHandDelay(); -- int
mob:GetHaste(); -- int
mob:GetHateAmount(Lua_Mob target); -- uint32
mob:GetHateAmount(Lua_Mob target, bool is_damage); -- uint32
mob:GetHateDamageTop(Lua_Mob other); -- Lua_Mob
mob:GetHateList(); -- Lua_HateList
mob:GetHateRandom(); -- Lua_Mob
mob:GetHateTop(); -- Lua_Mob
mob:GetHeading(); -- double
mob:GetHelmTexture(); -- int
mob:GetHerosForgeModel(uint8 material_slot); -- uint32
mob:GetINT(); -- int
mob:GetInvul(); -- bool
mob:GetItemBonuses(); -- Lua_StatBonuses
mob:GetItemHPBonuses(); -- int
mob:GetLevel(); -- int
mob:GetLevelCon(int my, int other); -- uint32
mob:GetLevelCon(int other); -- uint32
mob:GetLuclinFace(); -- int
mob:GetMR(); -- int
mob:GetMana(); -- int
mob:GetManaRatio(); -- double
mob:GetMaxAGI(); -- int
mob:GetMaxCHA(); -- int
mob:GetMaxDEX(); -- int
mob:GetMaxHP(); -- int
mob:GetMaxINT(); -- int
mob:GetMaxMana(); -- int
mob:GetMaxSTA(); -- int
mob:GetMaxSTR(); -- int
mob:GetMaxWIS(); -- int
mob:GetMeleeDamageMod_SE(uint16 skill); -- int16
mob:GetMeleeMinDamageMod_SE(uint16 skill); -- int16
mob:GetMeleeMitigation(); -- int32
mob:GetModSkillDmgTaken(int skill); -- int
mob:GetModVulnerability(int resist); -- int
mob:GetNPCTypeID(); -- int
mob:GetNimbusEffect1(); -- uint8
mob:GetNimbusEffect2(); -- uint8
mob:GetNimbusEffect3(); -- uint8
mob:GetOrigBodyType(); -- int
mob:GetOwner(); -- Lua_Mob
mob:GetPR(); -- int
mob:GetPet(); -- Lua_Mob
mob:GetPetOrder(); -- int
mob:GetPhR(); -- int
mob:GetRace(); -- int
mob:GetResist(int type); -- int
mob:GetReverseFactionCon(Lua_Mob other); -- int
mob:GetRunspeed(); -- double
mob:GetSTA(); -- int
mob:GetSTR(); -- int
mob:GetSize(); -- double
mob:GetSkill(int skill); -- int
mob:GetSkillDmgAmt(uint16 skill); -- int
mob:GetSkillDmgTaken(int skill); -- int
mob:GetSpecialAbility(int ability); -- int
mob:GetSpecialAbilityParam(int ability, int param); -- int
mob:GetSpecializeSkillValue(int spell_id); -- int
mob:GetSpellBonuses(); -- Lua_StatBonuses
mob:GetSpellHPBonuses(); -- int
mob:GetTarget(); -- Lua_Mob
mob:GetTexture(); -- int
mob:GetWIS(); -- int
mob:GetWalkspeed(); -- double
mob:GetWaypointH(); -- double
mob:GetWaypointID(); -- int
mob:GetWaypointPause(); -- double
mob:GetWaypointX(); -- double
mob:GetWaypointY(); -- double
mob:GetWaypointZ(); -- double
mob:GetWeaponDamage(Lua_Mob against, Lua_ItemInst weapon); -- int
mob:GetWeaponDamageBonus(Lua_Item weapon, bool offhand); -- int
mob:GetX(); -- double
mob:GetY(); -- double
mob:GetZ(); -- double
mob:GotoBind(); -- void
mob:HalveAggro(Lua_Mob other); -- void
mob:HasNPCSpecialAtk(const char *parse); -- bool
mob:HasOwner(); -- bool
mob:HasPet(); -- bool
mob:HasProcs(); -- bool
mob:HasShieldEquiped(); -- bool
mob:HasTwoHandBluntEquiped(); -- bool
mob:HasTwoHanderEquipped(); -- bool
mob:Heal(); -- void
mob:HealDamage(uint32 amount); -- void
mob:HealDamage(uint32 amount, Lua_Mob other); -- void
mob:InterruptSpell(); -- void
mob:InterruptSpell(int spell_id); -- void
mob:IsAIControlled(); -- bool
mob:IsAmnesiad(); -- bool
mob:IsAttackAllowed(Lua_Mob target, bool isSpellAttack); -- bool
mob:IsBeneficialAllowed(Lua_Mob target); -- bool
mob:IsBerserk(); -- bool
mob:IsBlind(); -- bool
mob:IsCasting(); -- bool
mob:IsEliteMaterialItem(uint8 material_slot); -- uint32
mob:IsEngaged(); -- bool
mob:IsEnraged(); -- bool
mob:IsFeared(); -- bool
mob:IsImmuneToSpell(int spell_id, Lua_Mob caster); -- bool
mob:IsInvisible(); -- bool
mob:IsInvisible(Lua_Mob other); -- bool
mob:IsMeleeDisabled(); -- bool
mob:IsMezzed(); -- bool
mob:IsMoving(); -- bool
mob:IsPet(); -- bool
mob:IsRoamer(); -- bool
mob:IsRooted(); -- bool
mob:IsRunning(); -- bool
mob:IsSilenced(); -- bool
mob:IsStunned(); -- bool
mob:IsTargetable(); -- bool
mob:IsTargeted(); -- bool
mob:IsWarriorClass(); -- bool
mob:Kill(); -- void
mob:Mesmerize(); -- void
mob:Message(int type, const char *message); -- void
mob:Message_StringID(int type, int string_id, uint32 distance); -- void
mob:ModSkillDmgTaken(int skill, int value); -- void
mob:ModVulnerability(int resist, int value); -- void
mob:NPCSpecialAttacks(const char *parse, int perm); -- void
mob:NPCSpecialAttacks(const char *parse, int perm, bool reset); -- void
mob:NPCSpecialAttacks(const char *parse, int perm, bool reset, bool remove); -- void
mob:ProcessSpecialAbilities(std::string str); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed, double angle); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed, double angle, double tilt); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed, double angle, double tilt, double arc); -- void
mob:QuestSay(Lua_Client client, const char *message); -- void
mob:RangedAttack(Lua_Mob other); -- void
mob:RemoveNimbusEffect(int effect_id); -- void
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster); -- double
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster, bool use_resist_override); -- double
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster, bool use_resist_override, int resist_override); -- double
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster, bool use_resist_override, int resist_override,; -- double
mob:Say(const char *message); -- void
mob:SeeHide(); -- bool
mob:SeeImprovedHide(); -- bool
mob:SeeInvisible(); -- uint8
mob:SeeInvisibleUndead(); -- bool
mob:SendAppearanceEffect(uint32 parm1, uint32 parm2, uint32 parm3, uint32 parm4, uint32 parm5); -- void
mob:SendAppearanceEffect(uint32 parm1, uint32 parm2, uint32 parm3, uint32 parm4, uint32 parm5, Lua_Client specific_target); -- void
mob:SendBeginCast(int spell_id, int cast_time); -- void
mob:SendSpellEffect(uint32 effect_id, uint32 duration, uint32 finish_delay, bool zone_wide, uint32 unk020); -- void
mob:SendSpellEffect(uint32 effect_id, uint32 duration, uint32 finish_delay, bool zone_wide, uint32 unk020, bool perm_effect); -- void
mob:SendSpellEffect(uint32 effect_id, uint32 duration, uint32 finish_delay, bool zone_wide, uint32 unk020, bool perm_effect,; -- void
mob:SendTo(double x, double y, double z); -- void
mob:SendToFixZ(double x, double y, double z); -- void
mob:SendWearChange(int material_slot); -- void
mob:SetAA(int rank_id, int new_value); -- bool
mob:SetAA(int rank_id, int new_value, int charges); -- bool
mob:SetAllowBeneficial(bool value); -- void
mob:SetAppearance(int app); -- void
mob:SetAppearance(int app, bool ignore_self); -- void
mob:SetBodyType(int new_body, bool overwrite_orig); -- void
mob:SetCurrentWP(int wp); -- void
mob:SetDestructibleObject(bool set); -- void
mob:SetDisableMelee(bool disable); -- void
mob:SetEntityVariable(const char *name, const char *value); -- void
mob:SetExtraHaste(int haste); -- void
mob:SetFlurryChance(int value); -- void
mob:SetFlyMode(int in); -- void
mob:SetGender(int in); -- void
mob:SetGlobal(const char *varname, const char *newvalue, int options, const char *duration); -- void
mob:SetGlobal(const char *varname, const char *newvalue, int options, const char *duration, Lua_Mob other); -- void
mob:SetHP(int hp); -- void
mob:SetHate(Lua_Mob other); -- void
mob:SetHate(Lua_Mob other, int hate); -- void
mob:SetHate(Lua_Mob other, int hate, int damage); -- void
mob:SetHeading(double in); -- void
mob:SetInvisible(int state); -- void
mob:SetInvul(bool value); -- void
mob:SetLevel(int level); -- void
mob:SetLevel(int level, bool command); -- void
mob:SetMana(int mana); -- int
mob:SetOOCRegen(int regen); -- void
mob:SetPetOrder(int order); -- void
mob:SetPseudoRoot(bool in); -- void
mob:SetRace(int in); -- void
mob:SetRunning(bool running); -- void
mob:SetSlotTint(int material_slot, int red_tint, int green_tint, int blue_tint); -- void
mob:SetSpecialAbility(int ability, int level); -- void
mob:SetSpecialAbilityParam(int ability, int param, int value); -- void
mob:SetTarget(Lua_Mob t); -- void
mob:SetTargetable(bool on); -- void
mob:SetTexture(int in); -- void
mob:Shout(const char *message); -- void
mob:Signal(uint32 id); -- void
mob:SpellEffect(Lua_Mob caster, int spell_id, double partial); -- void
mob:SpellFinished(int spell_id, Lua_Mob target); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used, uint32 inventory_slot); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used, uint32 inventory_slot, int resist_adjust); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used, uint32 inventory_slot, int resist_adjust, bool proc); -- bool
mob:Spin(); -- void
mob:Stun(int duration); -- void
mob:TarGlobal(const char *varname, const char *value, const char *duration, int npc_id, int char_id, int zone_id); -- void
mob:TempName(); -- void
mob:TempName(const char *newname); -- void
mob:ThrowingAttack(Lua_Mob other); -- void
mob:TryFinishingBlow(Lua_Mob defender, int &damage); -- bool
mob:TryMoveAlong(float distance, float angle); -- void
mob:TryMoveAlong(float distance, float angle, bool send); -- void
mob:UnStun(); -- void
mob:WearChange(int material_slot, int texture, uint32 color); -- void
mob:WipeHateList(); -- void
```

# Object
```lua
object:ClearUser(); -- void
object:Close(); -- void
object:Delete(); -- void
object:Delete(bool reset_state); -- void
object:DeleteItem(int index); -- void
object:Depop(); -- void
object:EntityVariableExists(const char *name); -- bool
object:GetDBID(); -- uint32
object:GetHeading(); -- float
object:GetID(); -- int
object:GetIcon(); -- uint32
object:GetItemID(); -- uint32
object:GetType(); -- uint32
object:GetX(); -- float
object:GetY(); -- float
object:GetZ(); -- float
object:IsGroundSpawn(); -- bool
object:Repop(); -- void
object:Save(); -- bool
object:SetEntityVariable(const char *name, const char *value); -- void
object:SetHeading(float h); -- void
object:SetID(int user); -- void
object:SetIcon(uint32 icon); -- void
object:SetItemID(uint32 item_id); -- void
object:SetLocation(float x, float y, float z); -- void
object:SetModelName(const char *name); -- void
object:SetType(uint32 type); -- void
object:SetX(float x); -- void
object:SetY(float y); -- void
object:SetZ(float z); -- void
object:StartDecay(); -- void
object:VarSave(); -- uint32
```

# NPC
```lua
npc:AI_SetRoambox(float dist, float max_x, float min_x, float max_y, float min_y); -- void
npc:AI_SetRoambox(float dist, float max_x, float min_x, float max_y, float min_y, uint32 delay, uint32 mindelay); -- void
npc:AddAISpell(int priority, int spell_id, int type, int mana_cost, int recast_delay, int resist_adjust); -- void
npc:AddAISpell(int priority, int spell_id, int type, int mana_cost, int recast_delay, int resist_adjust, int min_hp, int max_hp); -- void
npc:AddCash(int copper, int silver, int gold, int platinum); -- void
npc:AddItem(int item_id, int charges); -- void
npc:AddItem(int item_id, int charges, bool equip); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3, int aug4); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3, int aug4, int aug5); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3, int aug4, int aug5, int aug6); -- void
npc:AddLootTable(); -- void
npc:AddLootTable(int id); -- void
npc:AssignWaypoints(int grid); -- void
npc:CalculateNewWaypoint(); -- void
npc:CheckNPCFactionAlly(int faction); -- int
npc:ClearItemList(); -- void
npc:CountLoot(); -- int
npc:DisplayWaypointInfo(Lua_Client to); -- void
npc:DoClassAttacks(Lua_Mob target); -- void
npc:GetAccuracyRating(); -- int
npc:GetAttackDelay(); -- int
npc:GetAttackSpeed(); -- float
npc:GetAvoidanceRating(); -- int
npc:GetCopper(); -- uint32
npc:GetGold(); -- uint32
npc:GetGrid(); -- int
npc:GetGuardPointX(); -- float
npc:GetGuardPointY(); -- float
npc:GetGuardPointZ(); -- float
npc:GetLoottableID(); -- int
npc:GetMaxDMG(); -- uint32
npc:GetMaxDamage(int level); -- uint32
npc:GetMaxWp(); -- int
npc:GetMinDMG(); -- uint32
npc:GetNPCFactionID(); -- int
npc:GetNPCHate(Lua_Mob ent); -- int
npc:GetNPCSpellsID(); -- int
npc:GetPetSpellID(); -- int
npc:GetPlatinum(); -- uint32
npc:GetPrimSkill(); -- int
npc:GetPrimaryFaction(); -- int
npc:GetRawAC(); -- int
npc:GetScore(); -- int
npc:GetSecSkill(); -- int
npc:GetSilver(); -- uint32
npc:GetSlowMitigation(); -- float
npc:GetSp2(); -- uint32
npc:GetSpawnKillCount(); -- int
npc:GetSpawnPointH(); -- float
npc:GetSpawnPointID(); -- int
npc:GetSpawnPointX(); -- float
npc:GetSpawnPointY(); -- float
npc:GetSpawnPointZ(); -- float
npc:GetSpellFocusDMG(); -- int
npc:GetSpellFocusHeal(); -- int
npc:GetSwarmOwner(); -- int
npc:GetSwarmTarget(); -- int
npc:GetWaypointMax(); -- int
npc:IsAnimal(); -- bool
npc:IsGuarding(); -- bool
npc:IsOnHatelist(Lua_Mob ent); -- bool
npc:MerchantCloseShop(); -- void
npc:MerchantOpenShop(); -- void
npc:ModifyNPCStat(const char *stat, const char *value); -- void
npc:MoveTo(float x, float y, float z, float h, bool save); -- void
npc:NextGuardPosition(); -- void
npc:PauseWandering(int pause_time); -- void
npc:PickPocket(Lua_Client thief); -- void
npc:RemoveAISpell(int spell_id); -- void
npc:RemoveCash(); -- void
npc:RemoveItem(int item_id); -- void
npc:RemoveItem(int item_id, int quantity); -- void
npc:RemoveItem(int item_id, int quantity, int slot); -- void
npc:ResumeWandering(); -- void
npc:SaveGuardSpot(); -- void
npc:SaveGuardSpot(bool clear); -- void
npc:SetCopper(uint32 amt); -- void
npc:SetGold(uint32 amt); -- void
npc:SetGrid(int grid); -- void
npc:SetNPCFactionID(int id); -- void
npc:SetPetSpellID(int id); -- void
npc:SetPlatinum(uint32 amt); -- void
npc:SetPrimSkill(int skill_id); -- void
npc:SetSaveWaypoint(int wp); -- void
npc:SetSecSkill(int skill_id); -- void
npc:SetSilver(uint32 amt); -- void
npc:SetSp2(int sg2); -- void
npc:SetSpellFocusDMG(int focus); -- void
npc:SetSpellFocusHeal(int focus); -- void
npc:SetSwarmTarget(int target); -- void
npc:SetTaunting(bool t); -- void
npc:SetWaypointPause(); -- void
npc:Signal(int id); -- void
npc:StartSwarmTimer(uint32 duration); -- void
npc:StopWandering(); -- void
npc:UpdateWaypoint(int wp); -- void
```

# Spell
```lua
spell:GetAEDuration(); -- uint32
spell:GetAEMaxTargets(); -- int
spell:GetActivated(); -- int
spell:GetAllowRest(); -- bool
spell:GetAoeRange(); -- float
spell:GetBase(int i); -- int
spell:GetBase2(int i); -- int
spell:GetBaseDiff(); -- int
spell:GetBonusHate(); -- int
spell:GetBuffDuration(); -- uint32
spell:GetBuffdurationFormula(); -- uint32
spell:GetCanMGB(); -- int
spell:GetCastRestriction(); -- int
spell:GetCastTime(); -- uint32
spell:GetCastingAnim(); -- int
spell:GetClasses(int i); -- int
spell:GetComponentCounts(int i); -- int
spell:GetComponents(int i); -- int
spell:GetDamageShieldType(); -- int
spell:GetDeities(int i); -- int
spell:GetDescNum(); -- int
spell:GetDirectionalEnd(); -- float
spell:GetDirectionalStart(); -- float
spell:GetDisallowSit(); -- int
spell:GetDispelFlag(); -- int
spell:GetEffectDescNum(); -- int
spell:GetEffectID(int i); -- int
spell:GetEndurCost(); -- int
spell:GetEndurTimerIndex(); -- int
spell:GetEndurUpkeep(); -- int
spell:GetEnvironmentType(); -- int
spell:GetFormula(int i); -- int
spell:GetGoodEffect(); -- int
spell:GetHateAdded(); -- int
spell:GetID(); -- int
spell:GetInCombat(); -- bool
spell:GetMana(); -- int
spell:GetMax(int i); -- int
spell:GetMaxDist(); -- float
spell:GetMaxDistMod(); -- float
spell:GetMaxResist(); -- int
spell:GetMaxTargets(); -- int
spell:GetMinDist(); -- float
spell:GetMinDistMod(); -- float
spell:GetMinRange(); -- float
spell:GetMinResist(); -- int
spell:GetNimbusEffect(); -- int
spell:GetNoexpendReagent(int i); -- int
spell:GetNumHits(); -- int
spell:GetOutOfCombat(); -- bool
spell:GetPVPResistBase(); -- int
spell:GetPVPResistCalc(); -- int
spell:GetPVPResistCap(); -- int
spell:GetPersistDeath(); -- bool
spell:GetPowerfulFlag(); -- int
spell:GetPushBack(); -- float
spell:GetPushUp(); -- float
spell:GetRange(); -- float
spell:GetRecastTime(); -- uint32
spell:GetRecourseLink(); -- int
spell:GetRecoveryTime(); -- uint32
spell:GetResistDiff(); -- int
spell:GetResistType(); -- int
spell:GetShortBuffBox(); -- int
spell:GetSkill(); -- int
spell:GetSpellAffectIndex(); -- int
spell:GetSpellCategory(); -- int
spell:GetSpellGroup(); -- int
spell:GetTargetType(); -- int
spell:GetTimeOfDay(); -- int
spell:GetUninterruptable(); -- int
spell:GetViralTargets(); -- int
spell:GetViralTimer(); -- int
spell:GetZoneType(); -- int
```

# Client
```lua
client:AccountID(); -- uint32
client:AddAAPoints(int points); -- void
client:AddAlternateCurrencyValue(uint32 currency, int amount); -- void
client:AddCrystals(uint32 radiant, uint32 ebon); -- void
client:AddEXP(uint32 add_exp); -- void
client:AddEXP(uint32 add_exp, int conlevel); -- void
client:AddEXP(uint32 add_exp, int conlevel, bool resexp); -- void
client:AddLevelBasedExp(int exp_pct); -- void
client:AddLevelBasedExp(int exp_pct, int max_level); -- void
client:AddMoneyToPP(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, bool update_client); -- void
client:AddPVPPoints(uint32 points); -- void
client:AddSkill(int skill_id, int value); -- void
client:Admin(); -- int
client:AssignTask(int task, int npc_id); -- void
client:AssignTask(int task, int npc_id, bool enforce_level_requirement); -- void
client:AssignToInstance(int instance_id); -- void
client:AutoSplitEnabled(); -- bool
client:BreakInvis(); -- void
client:CalcATK(); -- int
client:CalcCurrentWeight(); -- int
client:CalcPriceMod(Lua_Mob other, bool reverse); -- float
client:CanHaveSkill(int skill_id); -- bool
client:ChangeLastName(const char *in); -- void
client:CharacterID(); -- uint32
client:CheckIncreaseSkill(int skill_id, Lua_Mob target); -- void
client:CheckIncreaseSkill(int skill_id, Lua_Mob target, int chance_mod); -- void
client:CheckSpecializeIncrease(int spell_id); -- void
client:ClearCompassMark(); -- void
client:ClearZoneFlag(int zone_id); -- void
client:Connected(); -- bool
client:DecreaseByID(uint32 type, int amt); -- bool
client:DeleteItemInInventory(int slot_id, int quantity); -- void
client:DeleteItemInInventory(int slot_id, int quantity, bool update_client); -- void
client:DisableAreaEndRegen(); -- void
client:DisableAreaHPRegen(); -- void
client:DisableAreaManaRegen(); -- void
client:DisableAreaRegens(); -- void
client:Disconnect(); -- void
client:DropItem(int slot_id); -- void
client:Duck(); -- void
client:EnableAreaEndRegen(int value); -- void
client:EnableAreaHPRegen(int value); -- void
client:EnableAreaManaRegen(int value); -- void
client:EnableAreaRegens(int value); -- void
client:Escape(); -- void
client:FailTask(int task); -- void
client:FilteredMessage(Mob *sender, uint32 type, int filter, const char *message); -- void
client:FindSpellBookSlotBySpellID(int spell_id); -- int
client:ForageItem(); -- void
client:ForageItem(bool guarantee); -- void
client:Freeze(); -- void
client:GetAAExp(); -- uint32
client:GetAAPercent(); -- uint32
client:GetAAPoints(); -- int
client:GetAccountAge(); -- int
client:GetAccountFlag(std::string flag); -- std::string
client:GetAggroCount(); -- int
client:GetAllMoney(); -- uint64
client:GetAnon(); -- bool
client:GetAugmentIDAt(int slot_id, int aug_slot); -- int
client:GetBaseAGI(); -- int
client:GetBaseCHA(); -- int
client:GetBaseDEX(); -- int
client:GetBaseFace(); -- int
client:GetBaseINT(); -- int
client:GetBaseSTA(); -- int
client:GetBaseSTR(); -- int
client:GetBaseWIS(); -- int
client:GetBindHeading(); -- float
client:GetBindHeading(int index); -- float
client:GetBindX(); -- float
client:GetBindX(int index); -- float
client:GetBindY(); -- float
client:GetBindY(int index); -- float
client:GetBindZ(); -- float
client:GetBindZ(int index); -- float
client:GetBindZoneID(); -- uint32
client:GetBindZoneID(int index); -- uint32
client:GetCarriedMoney(); -- uint64
client:GetCharacterFactionLevel(int faction_id); -- int
client:GetClientVersion(); -- int
client:GetClientVersionBit(); -- uint32
client:GetCorpseCount(); -- int
client:GetCorpseID(int corpse); -- int
client:GetCorpseItemAt(int corpse, int slot); -- int
client:GetDiscSlotBySpellID(int32 spell_id); -- int
client:GetDuelTarget(); -- int
client:GetEXP(); -- uint32
client:GetEbonCrystals(); -- uint32
client:GetEndurance(); -- int
client:GetEndurancePercent(); -- int
client:GetFace(); -- int
client:GetFactionLevel(uint32 char_id, uint32 npc_id, uint32 race, uint32 class_, uint32 deity, uint32 faction, Lua_NPC npc); -- int
client:GetFeigned(); -- bool
client:GetGM(); -- bool
client:GetGroup(); -- Lua_Group
client:GetGroupPoints(); -- uint32
client:GetHorseId(); -- int
client:GetHunger(); -- int
client:GetIP(); -- uint32
client:GetInstrumentMod(int spell_id); -- int
client:GetInventory(); -- Lua_Inventory
client:GetItemIDAt(int slot_id); -- int
client:GetLDoNLosses(); -- int
client:GetLDoNLossesTheme(int theme); -- int
client:GetLDoNPointsTheme(int theme); -- int
client:GetLDoNWins(); -- int
client:GetLDoNWinsTheme(int theme); -- int
client:GetLanguageSkill(int skill_id); -- int
client:GetMaxEndurance(); -- int
client:GetModCharacterFactionLevel(int faction); -- int
client:GetMoney(uint8 type, uint8 subtype); -- uint32
client:GetNextAvailableSpellBookSlot(); -- int
client:GetNextAvailableSpellBookSlot(int start); -- int
client:GetPVP(); -- bool
client:GetPVPPoints(); -- uint32
client:GetRadiantCrystals(); -- uint32
client:GetRaid(); -- Lua_Raid
client:GetRaidPoints(); -- uint32
client:GetRawItemAC(); -- int
client:GetRawSkill(int skill_id); -- int
client:GetSkillPoints(); -- int
client:GetSpentAA(); -- int
client:GetStartZone(); -- int
client:GetThirst(); -- int
client:GetTotalSecondsPlayed(); -- uint32
client:GetWeight(); -- int
client:GoFish(); -- void
client:GrantAlternateAdvancementAbility(int aa_id, int points); -- bool
client:GrantAlternateAdvancementAbility(int aa_id, int points, bool ignore_cost); -- bool
client:GuildID(); -- uint32
client:GuildRank(); -- int
client:HasSkill(int skill_id); -- bool
client:HasSpellScribed(int spell_id); -- bool
client:HasZoneFlag(int zone_id); -- bool
client:Hungry(); -- bool
client:InZone(); -- bool
client:IncStats(int type, int value); -- void
client:IncreaseLanguageSkill(int skill_id); -- void
client:IncreaseLanguageSkill(int skill_id, int value); -- void
client:IncreaseSkill(int skill_id); -- void
client:IncreaseSkill(int skill_id, int value); -- void
client:IncrementAA(int aa); -- void
client:IsDead(); -- bool
client:IsDueling(); -- bool
client:IsGrouped(); -- bool
client:IsLD(); -- bool
client:IsMedding(); -- bool
client:IsRaidGrouped(); -- bool
client:IsSitting(); -- bool
client:IsTaskActive(int task); -- bool
client:IsTaskActivityActive(int task, int activity); -- bool
client:IsTaskCompleted(int task); -- bool
client:KeyRingAdd(uint32 item); -- void
client:KeyRingCheck(uint32 item); -- bool
client:Kick(); -- void
client:LearnRecipe(uint32 recipe); -- void
client:LeaveGroup(); -- void
client:MarkSingleCompassLoc(float in_x, float in_y, float in_z); -- void
client:MarkSingleCompassLoc(float in_x, float in_y, float in_z, int count); -- void
client:MaxSkill(int skill_id); -- int
client:MemSpell(int spell_id, int slot); -- void
client:MemSpell(int spell_id, int slot, bool update_client); -- void
client:MovePC(int zone, float x, float y, float z, float heading); -- void
client:MovePCInstance(int zone, int instance, float x, float y, float z, float heading); -- void
client:NukeItem(uint32 item_num); -- void
client:NukeItem(uint32 item_num, int where_to_check); -- void
client:OpenLFGuildWindow(); -- void
client:PlayMP3(std::string file); -- void
client:PushItemOnCursor(Lua_ItemInst inst); -- bool
client:PutItemInInventory(int slot_id, Lua_ItemInst inst); -- bool
client:QuestReadBook(const char *text, int type); -- void
client:QuestReward(Lua_Mob target); -- void
client:QuestReward(Lua_Mob target, uint32 copper); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum, uint32 itemid); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum, uint32 itemid, uint32 exp); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum, uint32 itemid, uint32 exp, bool faction); -- void
client:QueuePacket(Lua_Packet app); -- void
client:QueuePacket(Lua_Packet app, bool ack_req); -- void
client:QueuePacket(Lua_Packet app, bool ack_req, int client_connection_status); -- void
client:QueuePacket(Lua_Packet app, bool ack_req, int client_connection_status, int filter); -- void
client:RefundAA(); -- void
client:ResetAA(); -- void
client:ResetTrade(); -- void
client:Save(); -- void
client:Save(int commit_now); -- void
client:SaveBackup(); -- void
client:ScribeSpell(int spell_id, int slot); -- void
client:ScribeSpell(int spell_id, int slot, bool update_client); -- void
client:SendColoredText(uint32 type, std::string msg); -- void
client:SendItemScale(Lua_ItemInst inst); -- void
client:SendMarqueeMessage(uint32 type, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, std::string msg); -- void
client:SendOPTranslocateConfirm(Lua_Mob caster, int spell_id); -- void
client:SendSound(); -- void
client:SendWebLink(const char *site); -- void
client:SendZoneFlagInfo(Lua_Client to); -- void
client:SetAAPoints(int points); -- void
client:SetAATitle(const char *title); -- void
client:SetAccountFlag(std::string flag, std::string val); -- void
client:SetBaseClass(int v); -- void
client:SetBaseGender(int v); -- void
client:SetBaseRace(int v); -- void
client:SetBindPoint(); -- void
client:SetBindPoint(int to_zone); -- void
client:SetBindPoint(int to_zone, int to_instance); -- void
client:SetBindPoint(int to_zone, int to_instance, float new_x); -- void
client:SetBindPoint(int to_zone, int to_instance, float new_x, float new_y); -- void
client:SetBindPoint(int to_zone, int to_instance, float new_x, float new_y, float new_z); -- void
client:SetConsumption(int in_hunger, int in_thirst); -- void
client:SetDeity(int v); -- void
client:SetDuelTarget(int c); -- void
client:SetDueling(bool v); -- void
client:SetEXP(uint32 set_exp, uint32 set_aaxp); -- void
client:SetEXP(uint32 set_exp, uint32 set_aaxp, bool resexp); -- void
client:SetEndurance(int endur); -- void
client:SetFactionLevel(uint32 char_id, uint32 npc_id, int char_class, int char_race, int char_deity); -- void
client:SetFactionLevel2(uint32 char_id, int faction_id, int char_class, int char_race, int char_deity, int value, int temp); -- void
client:SetFeigned(bool v); -- void
client:SetGM(bool v); -- void
client:SetHorseId(int id); -- void
client:SetHunger(int in_hunger); -- void
client:SetLanguageSkill(int language, int value); -- void
client:SetMaterial(int slot_id, uint32 item_id); -- void
client:SetPVP(bool v); -- void
client:SetSkill(int skill_id, int value); -- void
client:SetSkillPoints(int skill); -- void
client:SetStartZone(int zone_id); -- void
client:SetStartZone(int zone_id, float x); -- void
client:SetStartZone(int zone_id, float x, float y); -- void
client:SetStartZone(int zone_id, float x, float y, float z); -- void
client:SetStats(int type, int value); -- void
client:SetThirst(int in_thirst); -- void
client:SetTint(int slot_id, uint32 color); -- void
client:SetTitleSuffix(const char *text); -- void
client:SetZoneFlag(int zone_id); -- void
client:Signal(uint32 id); -- void
client:Stand(); -- void
client:SummonItem(uint32 item_id); -- void
client:SummonItem(uint32 item_id, int charges); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5, bool attuned); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5, bool attuned, int to_slot); -- void
client:TGB(); -- bool
client:TakeMoneyFromPP(uint64 copper); -- bool
client:TakeMoneyFromPP(uint64 copper, bool update_client); -- bool
client:Thirsty(); -- bool
client:TrainDisc(int itemid); -- void
client:TrainDiscBySpellID(int32 spell_id); -- void
client:UnFreeze(); -- void
client:Undye(); -- void
client:UnmemSpell(int slot); -- void
client:UnmemSpell(int slot, bool update_client); -- void
client:UnmemSpellAll(); -- void
client:UnmemSpellAll(bool update_client); -- void
client:UnmemSpellBySpellID(int32 spell_id); -- void
client:UnscribeSpell(int slot); -- void
client:UnscribeSpell(int slot, bool update_client); -- void
client:UnscribeSpellAll(); -- void
client:UnscribeSpellAll(bool update_client); -- void
client:UntrainDisc(int slot); -- void
client:UntrainDisc(int slot, bool update_client); -- void
client:UntrainDiscAll(); -- void
client:UntrainDiscAll(bool update_client); -- void
client:UpdateGroupAAs(int points, uint32 type); -- void
client:UpdateLDoNPoints(int points, uint32 theme); -- void
client:UpdateTaskActivity(int task, int activity, int count); -- void
client:UseDiscipline(int spell_id, int target_id); -- bool
client:WorldKick(); -- void
```

# Item
```lua
item:GetAAgi(); -- int
item:GetAC(); -- int
item:GetACha(); -- int
item:GetADex(); -- int
item:GetAInt(); -- int
item:GetASta(); -- int
item:GetAStr(); -- int
item:GetAWis(); -- int
item:GetAccuracy(); -- int
item:GetArtifactFlag(); -- bool
item:GetAttack(); -- uint32
item:GetAttuneable(); -- bool
item:GetAugDistiller(); -- uint32
item:GetAugRestrict(); -- uint32
item:GetAugSlotType(int i); -- int
item:GetAugSlotUnk2(int i); -- int
item:GetAugSlotVisible(int i); -- int
item:GetAugType(); -- uint32
item:GetAvoidance(); -- int
item:GetBackstabDmg(); -- uint32
item:GetBagSize(); -- int
item:GetBagSlots(); -- int
item:GetBagType(); -- int
item:GetBagWR(); -- int
item:GetBaneDmgAmt(); -- int
item:GetBaneDmgBody(); -- uint32
item:GetBaneDmgRace(); -- uint32
item:GetBaneDmgRaceAmt(); -- uint32
item:GetBardType(); -- uint32
item:GetBardValue(); -- int
item:GetBard_Effect(); -- int
item:GetBard_Level(); -- int
item:GetBard_Level2(); -- int
item:GetBard_Type(); -- int
item:GetBenefitFlag(); -- bool
item:GetBook(); -- int
item:GetBookType(); -- uint32
item:GetCR(); -- int
item:GetCastTime(); -- int
item:GetCastTime_(); -- int
item:GetCharmFileID(); -- uint32
item:GetClairvoyance(); -- uint32
item:GetClasses(); -- uint32
item:GetClick_Effect(); -- int
item:GetClick_Level(); -- int
item:GetClick_Level2(); -- int
item:GetClick_Type(); -- int
item:GetColor(); -- uint32
item:GetCombatEffects(); -- int
item:GetDR(); -- int
item:GetDSMitigation(); -- uint32
item:GetDamage(); -- uint32
item:GetDamageShield(); -- uint32
item:GetDeity(); -- uint32
item:GetDelay(); -- int
item:GetDotShielding(); -- uint32
item:GetElemDmgAmt(); -- int
item:GetElemDmgType(); -- int
item:GetEliteMaterial(); -- uint32
item:GetEndur(); -- uint32
item:GetEnduranceRegen(); -- uint32
item:GetExpendableArrow(); -- int
item:GetExtraDmgAmt(); -- uint32
item:GetExtraDmgSkill(); -- uint32
item:GetFR(); -- int
item:GetFVNoDrop(); -- int
item:GetFactionAmt1(); -- int
item:GetFactionAmt2(); -- int
item:GetFactionAmt3(); -- int
item:GetFactionAmt4(); -- int
item:GetFactionMod1(); -- int
item:GetFactionMod2(); -- int
item:GetFactionMod3(); -- int
item:GetFactionMod4(); -- int
item:GetFavor(); -- uint32
item:GetFocus_Effect(); -- int
item:GetFocus_Level(); -- int
item:GetFocus_Level2(); -- int
item:GetFocus_Type(); -- int
item:GetFulfilment(); -- uint32
item:GetGuildFavor(); -- uint32
item:GetHP(); -- int
item:GetHaste(); -- uint32
item:GetHealAmt(); -- int
item:GetHeroicAgi(); -- int
item:GetHeroicCR(); -- int
item:GetHeroicCha(); -- int
item:GetHeroicDR(); -- int
item:GetHeroicDex(); -- int
item:GetHeroicFR(); -- int
item:GetHeroicInt(); -- int
item:GetHeroicMR(); -- int
item:GetHeroicPR(); -- int
item:GetHeroicSVCorrup(); -- int
item:GetHeroicSta(); -- int
item:GetHeroicStr(); -- int
item:GetHeroicWis(); -- int
item:GetID(); -- uint32
item:GetIcon(); -- uint32
item:GetItemClass(); -- int
item:GetItemType(); -- int
item:GetLDoNPrice(); -- uint32
item:GetLDoNSellBackRate(); -- uint32
item:GetLDoNSold(); -- uint32
item:GetLDoNTheme(); -- uint32
item:GetLight(); -- int
item:GetLoreFlag(); -- bool
item:GetLoreGroup(); -- uint32
item:GetMR(); -- int
item:GetMagic(); -- bool
item:GetMana(); -- int
item:GetManaRegen(); -- uint32
item:GetMaterial(); -- int
item:GetMaxCharges(); -- int
item:GetMinStatus(); -- int
item:GetNoDrop(); -- int
item:GetNoPet(); -- bool
item:GetNoRent(); -- int
item:GetNoTransfer(); -- bool
item:GetPR(); -- int
item:GetPendingLoreFlag(); -- bool
item:GetPointType(); -- uint32
item:GetPotionBelt(); -- bool
item:GetPotionBeltSlots(); -- int
item:GetPrice(); -- uint32
item:GetProcRate(); -- int
item:GetProc_Effect(); -- int
item:GetProc_Level(); -- int
item:GetProc_Level2(); -- int
item:GetProc_Type(); -- int
item:GetPurity(); -- uint32
item:GetQuestItemFlag(); -- bool
item:GetRaces(); -- uint32
item:GetRange(); -- int
item:GetRecLevel(); -- int
item:GetRecSkill(); -- int
item:GetRecastDelay(); -- uint32
item:GetRecastType(); -- uint32
item:GetRegen(); -- uint32
item:GetReqLevel(); -- int
item:GetSVCorruption(); -- int
item:GetScriptFileID(); -- uint32
item:GetScroll_Effect(); -- int
item:GetScroll_Level(); -- int
item:GetScroll_Level2(); -- int
item:GetScroll_Type(); -- int
item:GetSellRate(); -- double
item:GetShielding(); -- int
item:GetSize(); -- int
item:GetSkillModType(); -- uint32
item:GetSkillModValue(); -- int
item:GetSlots(); -- uint32
item:GetSpellDmg(); -- int
item:GetSpellShield(); -- int
item:GetStackSize(); -- int
item:GetStackable(); -- bool
item:GetStrikeThrough(); -- int
item:GetStunResist(); -- int
item:GetSummonedFlag(); -- bool
item:GetTradeskills(); -- bool
item:GetWeight(); -- int
item:GetWorn_Effect(); -- int
item:GetWorn_Level(); -- int
item:GetWorn_Level2(); -- int
item:GetWorn_Type(); -- int
```

# HateEntry
```lua
hate_entry:GetDamage(); -- int
hate_entry:GetEnt(); -- Lua_Mob
hate_entry:GetFrenzy(); -- int
hate_entry:GetHate(); -- int
hate_entry:SetDamage(int value); -- void
hate_entry:SetEnt(Lua_Mob e); -- void
hate_entry:SetFrenzy(bool value); -- void
hate_entry:SetHate(int value); -- void
```

# Door
```lua
door:CreateDatabaseEntry(); -- void
door:ForceClose(Lua_Mob sender); -- void
door:ForceClose(Lua_Mob sender, bool alt_mode); -- void
door:ForceOpen(Lua_Mob sender); -- void
door:ForceOpen(Lua_Mob sender, bool alt_mode); -- void
door:GetDisableTimer(); -- bool
door:GetDoorDBID(); -- uint32
door:GetDoorID(); -- uint32
door:GetHeading(); -- float
door:GetIncline(); -- uint32
door:GetKeyItem(); -- uint32
door:GetLockPick(); -- uint32
door:GetNoKeyring(); -- int
door:GetOpenType(); -- uint32
door:GetSize(); -- uint32
door:GetX(); -- float
door:GetY(); -- float
door:GetZ(); -- float
door:SetDisableTimer(bool flag); -- void
door:SetDoorName(const char *name); -- void
door:SetHeading(float h); -- void
door:SetIncline(uint32 incline); -- void
door:SetKeyItem(uint32 key); -- void
door:SetLocation(float x, float y, float z); -- void
door:SetLockPick(uint32 pick); -- void
door:SetNoKeyring(int type); -- void
door:SetOpenType(uint32 type); -- void
door:SetSize(uint32 sz); -- void
door:SetX(float x); -- void
door:SetY(float y); -- void
door:SetZ(float z); -- void
```

# Entity
```lua
entity:CastToClient(); -- Lua_Client
entity:CastToCorpse(); -- Lua_Corpse
entity:CastToDoor(); -- Lua_Door
entity:CastToMob(); -- Lua_Mob
entity:CastToNPC(); -- Lua_NPC
entity:CastToObject(); -- Lua_Object
entity:GetID(); -- int
entity:IsBeacon(); -- bool
entity:IsBot(); -- bool
entity:IsClient(); -- bool
entity:IsCorpse(); -- bool
entity:IsDoor(); -- bool
entity:IsEncounter(); -- bool
entity:IsMerc(); -- bool
entity:IsMob(); -- bool
entity:IsNPC(); -- bool
entity:IsNPCCorpse(); -- bool
entity:IsObject(); -- bool
entity:IsPlayerCorpse(); -- bool
entity:IsTrap(); -- bool
```

# Inventory
```lua
inventory:CalcBagIdx(int slot_id); -- int
inventory:CalcMaterialFromSlot(int equipslot); -- int
inventory:CalcSlotFromMaterial(int material); -- int
inventory:CalcSlotId(int slot_id); -- int
inventory:CalcSlotId(int slot_id, int bag_slot); -- int
inventory:CanItemFitInContainer(Lua_Item item, Lua_Item container); -- bool
inventory:CheckNoDrop(int slot_id); -- bool
inventory:DeleteItem(int slot_id); -- bool
inventory:DeleteItem(int slot_id, int quantity); -- bool
inventory:FindFreeSlot(bool for_bag, bool try_cursor); -- int
inventory:FindFreeSlot(bool for_bag, bool try_cursor, int min_size); -- int
inventory:FindFreeSlot(bool for_bag, bool try_cursor, int min_size, bool is_arrow); -- int
inventory:GetItem(int slot_id); -- Lua_ItemInst
inventory:GetItem(int slot_id, int bag_slot); -- Lua_ItemInst
inventory:GetSlotByItemInst(Lua_ItemInst inst); -- int
inventory:HasItem(int item_id); -- int
inventory:HasItem(int item_id, int quantity); -- int
inventory:HasItem(int item_id, int quantity, int where); -- int
inventory:HasItemByLoreGroup(uint32 loregroup); -- int
inventory:HasItemByLoreGroup(uint32 loregroup, int where); -- int
inventory:HasItemByUse(int use); -- int
inventory:HasItemByUse(int use, uint8 quantity); -- int
inventory:HasItemByUse(int use, uint8 quantity, uint8 where); -- int
inventory:HasSpaceForItem(Lua_Item item, int quantity); -- bool
inventory:PopItem(int slot_id); -- Lua_ItemInst
inventory:PushCursor(Lua_ItemInst item); -- int
inventory:PutItem(int slot_id, Lua_ItemInst item); -- int
inventory:SupportsContainers(int slot_id); -- bool
inventory:SwapItem(int slot_a, int slot_b); -- bool
```

# EntityList
```lua
entity_list:CanAddHateForMob(Lua_Mob p); -- bool
entity_list:ChannelMessage(Lua_Mob from, int channel_num, int language, const char *message); -- void
entity_list:ClearClientPetitionQueue(); -- void
entity_list:ClearFeignAggro(Lua_Mob who); -- void
entity_list:DeleteNPCCorpses(); -- int
entity_list:DeletePlayerCorpses(); -- int
entity_list:DoubleAggro(Lua_Mob who); -- void
entity_list:Fighting(Lua_Mob who); -- bool
entity_list:FilteredMessageClose(Lua_Mob sender, bool skip_sender, float dist, uint32 type, int filter, const char *message); -- void
entity_list:FindDoor(uint32 id); -- Lua_Door
entity_list:GetClientByAccID(uint32 acct_id); -- Lua_Client
entity_list:GetClientByCharID(uint32 char_id); -- Lua_Client
entity_list:GetClientByID(int id); -- Lua_Client
entity_list:GetClientByName(const char *name); -- Lua_Client
entity_list:GetClientByWID(uint32 wid); -- Lua_Client
entity_list:GetClientList(); -- Lua_Client_List
entity_list:GetCorpseByID(int id); -- Lua_Corpse
entity_list:GetCorpseByName(const char *name); -- Lua_Corpse
entity_list:GetCorpseByOwner(Lua_Client client); -- Lua_Corpse
entity_list:GetCorpseList(); -- Lua_Corpse_List
entity_list:GetDoorsByDBID(uint32 db_id); -- Lua_Door
entity_list:GetDoorsByDoorID(uint32 door_id); -- Lua_Door
entity_list:GetDoorsByID(int id); -- Lua_Door
entity_list:GetDoorsList(); -- Lua_Doors_List
entity_list:GetGroupByClient(Lua_Client client); -- Lua_Group
entity_list:GetGroupByID(int id); -- Lua_Group
entity_list:GetGroupByLeaderName(const char *name); -- Lua_Group
entity_list:GetGroupByMob(Lua_Mob mob); -- Lua_Group
entity_list:GetMob(const char *name); -- Lua_Mob
entity_list:GetMob(int id); -- Lua_Mob
entity_list:GetMobByNpcTypeID(int npc_type); -- Lua_Mob
entity_list:GetMobID(int id); -- Lua_Mob
entity_list:GetMobList(); -- Lua_Mob_List
entity_list:GetNPCByID(int id); -- Lua_NPC
entity_list:GetNPCByNPCTypeID(int npc_type); -- Lua_NPC
entity_list:GetNPCList(); -- Lua_NPC_List
entity_list:GetObjectByDBID(uint32 db_id); -- Lua_Object
entity_list:GetObjectByID(int id); -- Lua_Object
entity_list:GetObjectList(); -- Lua_Object_List
entity_list:GetRaidByClient(Lua_Client client); -- Lua_Raid
entity_list:GetRaidByID(int id); -- Lua_Raid
entity_list:GetRandomClient(float x, float y, float z, float dist); -- Lua_Client
entity_list:GetRandomClient(float x, float y, float z, float dist, Lua_Client exclude); -- Lua_Client
entity_list:GetSpawnByID(uint32 id); -- Lua_Spawn
entity_list:GetSpawnList(); -- Lua_Spawn_List
entity_list:HalveAggro(Lua_Mob who); -- void
entity_list:IsMobSpawnedByNpcTypeID(int npc_type); -- bool
entity_list:MakeNameUnique(const char *name); -- std::string
entity_list:Message(uint32 guild_dbid, uint32 type, const char *message); -- void
entity_list:MessageClose(Lua_Mob sender, bool skip_sender, float dist, uint32 type, const char *message); -- void
entity_list:MessageGroup(Lua_Mob who, bool skip_close, uint32 type, const char *message); -- void
entity_list:MessageStatus(uint32 guild_dbid, int min_status, uint32 type, const char *message); -- void
entity_list:OpenDoorsNear(Lua_NPC opener); -- void
entity_list:RemoveFromHateLists(Lua_Mob who); -- void
entity_list:RemoveFromHateLists(Lua_Mob who, bool set_to_one); -- void
entity_list:RemoveFromTargets(Lua_Mob mob); -- void
entity_list:RemoveFromTargets(Lua_Mob mob, bool RemoveFromXTargets); -- void
entity_list:RemoveNumbers(const char *name); -- std::string
entity_list:ReplaceWithTarget(Lua_Mob target, Lua_Mob new_target); -- void
entity_list:SignalAllClients(int signal); -- void
entity_list:SignalMobsByNPCID(uint32 npc_id, int signal); -- void
```

# Spawn
```lua
spawn:CurrentNPCID(); -- uint32
spawn:Depop(); -- void
spawn:Disable(); -- void
spawn:Enable(); -- void
spawn:Enabled(); -- bool
spawn:ForceDespawn(); -- void
spawn:GetHeading(); -- float
spawn:GetID(); -- uint32
spawn:GetKillCount(); -- uint32
spawn:GetSpawnCondition(); -- uint32
spawn:GetVariance(); -- uint32
spawn:GetX(); -- float
spawn:GetY(); -- float
spawn:GetZ(); -- float
spawn:LoadGrid(); -- void
spawn:NPCPointerValid(); -- bool
spawn:Repop(); -- void
spawn:Repop(uint32 delay); -- void
spawn:Reset(); -- void
spawn:RespawnTimer(); -- uint32
spawn:SetCurrentNPCID(uint32 nid); -- void
spawn:SetNPCPointer(Lua_NPC n); -- void
spawn:SetRespawnTimer(uint32 newrespawntime); -- void
spawn:SetTimer(uint32 duration); -- void
spawn:SetVariance(uint32 newvariance); -- void
spawn:SpawnGroupID(); -- uint32
```

# StatBonuses
```lua
statbonuses:GetAC() const; -- int32
statbonuses:GetAGI() const; -- int32
statbonuses:GetAGICapMod() const; -- int32
statbonuses:GetAStacker(int idx) const; -- int32
statbonuses:GetATK() const; -- int32
statbonuses:GetAbsorbMagicAtt(int idx) const; -- uint32
statbonuses:GetAccuracy(int idx) const; -- int32
statbonuses:GetAggroRange() const; -- float
statbonuses:GetAlterNPCLevel() const; -- int32
statbonuses:GetAmbidexterity() const; -- int32
statbonuses:GetAmplification() const; -- uint32
statbonuses:GetAntiGate() const; -- bool
statbonuses:GetArcheryDamageModifier() const; -- uint32
statbonuses:GetAssassinate(int idx) const; -- uint32
statbonuses:GetAssassinateLevel(int idx) const; -- uint8
statbonuses:GetAssistRange() const; -- float
statbonuses:GetAvoidMeleeChance() const; -- int32
statbonuses:GetAvoidMeleeChanceEffect() const; -- int32
statbonuses:GetBStacker(int idx) const; -- int32
statbonuses:GetBaseMovementSpeed() const; -- int8
statbonuses:GetBerserkSPA() const; -- bool
statbonuses:GetBindWound() const; -- int32
statbonuses:GetBlockBehind() const; -- int32
statbonuses:GetBlockNextSpell() const; -- bool
statbonuses:GetBuffSlotIncrease() const; -- uint8
statbonuses:GetCHA() const; -- int32
statbonuses:GetCHACapMod() const; -- int32
statbonuses:GetCR() const; -- int32
statbonuses:GetCRCapMod() const; -- int32
statbonuses:GetCStacker(int idx) const; -- int32
statbonuses:GetChannelChanceItems() const; -- int32
statbonuses:GetChannelChanceSpells() const; -- int32
statbonuses:GetCharmBreakChance() const; -- int32
statbonuses:GetClairvoyance() const; -- int32
statbonuses:GetCombatStability() const; -- int32
statbonuses:GetConsumeProjectile() const; -- uint8
statbonuses:GetCorrup() const; -- int32
statbonuses:GetCorrupCapMod() const; -- int32
statbonuses:GetCrippBlowChance() const; -- int32
statbonuses:GetCritDmgMod(int idx) const; -- int32
statbonuses:GetCriticalDoTChance() const; -- int32
statbonuses:GetCriticalDotDecay() const; -- bool
statbonuses:GetCriticalHealChance() const; -- int32
statbonuses:GetCriticalHealDecay() const; -- bool
statbonuses:GetCriticalHealOverTime() const; -- int32
statbonuses:GetCriticalHitChance(int idx) const; -- int32
statbonuses:GetCriticalMend() const; -- int8
statbonuses:GetCriticalRegenDecay() const; -- bool
statbonuses:GetCriticalSpellChance() const; -- int32
statbonuses:GetDEX() const; -- int32
statbonuses:GetDEXCapMod() const; -- int32
statbonuses:GetDR() const; -- int32
statbonuses:GetDRCapMod() const; -- int32
statbonuses:GetDSMitigation() const; -- int32
statbonuses:GetDSMitigationOffHand() const; -- int32
statbonuses:GetDStacker(int idx) const; -- int32
statbonuses:GetDamageModifier(int idx) const; -- int32
statbonuses:GetDamageModifier2(int idx) const; -- int32
statbonuses:GetDamageShield() const; -- int
statbonuses:GetDamageShieldSpellID() const; -- uint16
statbonuses:GetDamageShieldType() const; -- int
statbonuses:GetDeathSave(int idx) const; -- uint32
statbonuses:GetDelayDeath() const; -- uint32
statbonuses:GetDistanceRemoval() const; -- bool
statbonuses:GetDivineAura() const; -- bool
statbonuses:GetDivineSaveChance(int idx) const; -- int32
statbonuses:GetDoTShielding() const; -- int32
statbonuses:GetDodgeChance() const; -- int32
statbonuses:GetDotCritDmgIncrease() const; -- int32
statbonuses:GetDoubleAttackChance() const; -- int32
statbonuses:GetDoubleRangedAttack() const; -- int32
statbonuses:GetDoubleRiposte() const; -- int32
statbonuses:GetDoubleSpecialAttack() const; -- int32
statbonuses:GetDualWieldChance() const; -- int32
statbonuses:GetEndPercCap(int idx) const; -- int
statbonuses:GetEndurance() const; -- int32
statbonuses:GetEnduranceReduction() const; -- int32
statbonuses:GetEnduranceRegen() const; -- int32
statbonuses:GetExtraAttackChance() const; -- int32
statbonuses:GetFR() const; -- int32
statbonuses:GetFRCapMod() const; -- int32
statbonuses:GetFactionModPct() const; -- int32
statbonuses:GetFearless() const; -- bool
statbonuses:GetFeignedCastOnChance() const; -- int16
statbonuses:GetFinishingBlow(int idx) const; -- int32
statbonuses:GetFinishingBlowLvl(int idx) const; -- uint32
statbonuses:GetFlurryChance() const; -- int32
statbonuses:GetFocusEffects(int idx) const; -- uint8
statbonuses:GetFocusEffectsWorn(int idx) const; -- int16
statbonuses:GetForageAdditionalItems() const; -- uint8
statbonuses:GetFrenziedDevastation() const; -- int32
statbonuses:GetFrontalBackstabChance() const; -- uint8
statbonuses:GetFrontalBackstabMinDmg() const; -- bool
statbonuses:GetFrontalStunResist() const; -- uint8
statbonuses:GetGiveDoubleAttack() const; -- uint32
statbonuses:GetGiveDoubleRiposte(int idx) const; -- int32
statbonuses:GetGivePetGroupTarget() const; -- bool
statbonuses:GetGravityEffect() const; -- int32
statbonuses:GetHP() const; -- int32
statbonuses:GetHPPercCap(int idx) const; -- int
statbonuses:GetHPRegen() const; -- int32
statbonuses:GetHPToManaConvert() const; -- uint32
statbonuses:GetHSLevel(int idx) const; -- uint8
statbonuses:GetHeadShot(int idx) const; -- uint32
statbonuses:GetHealAmt() const; -- int32
statbonuses:GetHealRate() const; -- int32
statbonuses:GetHeroicAGI() const; -- int32
statbonuses:GetHeroicCHA() const; -- int32
statbonuses:GetHeroicCR() const; -- int32
statbonuses:GetHeroicCorrup() const; -- int32
statbonuses:GetHeroicDEX() const; -- int32
statbonuses:GetHeroicDR() const; -- int32
statbonuses:GetHeroicFR() const; -- int32
statbonuses:GetHeroicINT() const; -- int32
statbonuses:GetHeroicMR() const; -- int32
statbonuses:GetHeroicPR() const; -- int32
statbonuses:GetHeroicSTA() const; -- int32
statbonuses:GetHeroicSTR() const; -- int32
statbonuses:GetHeroicWIS() const; -- int32
statbonuses:GetHitChance() const; -- int32
statbonuses:GetHitChanceEffect(int idx) const; -- int32
statbonuses:GetHundredHands() const; -- int32
statbonuses:GetINT() const; -- int32
statbonuses:GetINTCapMod() const; -- int32
statbonuses:GetIllusionPersistence() const; -- bool
statbonuses:GetImmuneToFlee() const; -- bool
statbonuses:GetImprovedReclaimEnergy() const; -- int32
statbonuses:GetImprovedTaunt(int idx) const; -- int32
statbonuses:GetIncreaseBlockChance() const; -- int32
statbonuses:GetIncreaseChanceMemwipe() const; -- int8
statbonuses:GetIncreaseRunSpeedCap() const; -- uint8
statbonuses:GetIsBlind() const; -- bool
statbonuses:GetIsFeared() const; -- bool
statbonuses:GetItemATKCap() const; -- int32
statbonuses:GetItemHPRegenCap() const; -- int32
statbonuses:GetItemManaRegenCap() const; -- uint32
statbonuses:GetLimitToSkill(int idx) const; -- bool
statbonuses:GetMR() const; -- int32
statbonuses:GetMRCapMod() const; -- int32
statbonuses:GetMagicWeapon() const; -- bool
statbonuses:GetMana() const; -- int32
statbonuses:GetManaAbsorbPercentDamage(int idx) const; -- uint32
statbonuses:GetManaPercCap(int idx) const; -- int
statbonuses:GetManaRegen() const; -- int32
statbonuses:GetMasteryofPast() const; -- uint8
statbonuses:GetMaxBindWound() const; -- int32
statbonuses:GetMaxHP() const; -- int32
statbonuses:GetMaxHPChange() const; -- int32
statbonuses:GetMeleeLifetap() const; -- int32
statbonuses:GetMeleeMitigation() const; -- int32
statbonuses:GetMeleeMitigationEffect() const; -- int32
statbonuses:GetMeleeRune(int idx) const; -- uint32
statbonuses:GetMeleeSkillCheck() const; -- int32
statbonuses:GetMeleeSkillCheckSkill() const; -- uint8
statbonuses:GetMeleeThresholdGuard(int idx) const; -- uint32
statbonuses:GetMetabolism() const; -- int32
statbonuses:GetMinDamageModifier(int idx) const; -- int32
statbonuses:GetMitigateDotRune(int idx) const; -- uint32
statbonuses:GetMitigateMeleeRune(int idx) const; -- uint32
statbonuses:GetMitigateSpellRune(int idx) const; -- uint32
statbonuses:GetNegateAttacks(int idx) const; -- uint32
statbonuses:GetNegateEffects() const; -- bool
statbonuses:GetNegateIfCombat() const; -- bool
statbonuses:GetNoBreakAESneak() const; -- int16
statbonuses:GetOffhandRiposteFail() const; -- int32
statbonuses:GetPC_Pet_Flurry() const; -- uint32
statbonuses:GetPC_Pet_Rampage(int idx) const; -- uint32
statbonuses:GetPR() const; -- int32
statbonuses:GetPRCapMod() const; -- int32
statbonuses:GetPackrat() const; -- int8
statbonuses:GetParryChance() const; -- int32
statbonuses:GetPersistantCasting() const; -- uint32
statbonuses:GetPetAvoidance() const; -- int32
statbonuses:GetPetCriticalHit() const; -- int32
statbonuses:GetPetFlurry() const; -- int32
statbonuses:GetPetMaxHP() const; -- int32
statbonuses:GetPetMeleeMitigation() const; -- int32
statbonuses:GetProcChance() const; -- int32
statbonuses:GetProcChanceSPA() const; -- int32
statbonuses:GetRaiseSkillCap(int idx) const; -- uint32
statbonuses:GetReduceFallDamage() const; -- uint16
statbonuses:GetReduceTradeskillFail(int idx) const; -- int32
statbonuses:GetResistFearChance() const; -- int32
statbonuses:GetResistSpellChance() const; -- int32
statbonuses:GetReverseDamageShield() const; -- int
statbonuses:GetReverseDamageShieldSpellID() const; -- uint16
statbonuses:GetReverseDamageShieldType() const; -- int
statbonuses:GetRiposteChance() const; -- int32
statbonuses:GetRoot(int idx) const; -- int8
statbonuses:GetRootBreakChance() const; -- int32
statbonuses:GetSEResist(int idx) const; -- int32
statbonuses:GetSTA() const; -- int32
statbonuses:GetSTACapMod() const; -- int32
statbonuses:GetSTR() const; -- int32
statbonuses:GetSTRCapMod() const; -- int32
statbonuses:GetSalvageChance() const; -- uint8
statbonuses:GetSanctuary() const; -- bool
statbonuses:GetScreech() const; -- int8
statbonuses:GetSecondaryDmgInc() const; -- bool
statbonuses:GetSeeInvis() const; -- uint8
statbonuses:GetShieldBlock() const; -- int32
statbonuses:GetShieldEquipDmgMod() const; -- int32
statbonuses:GetShroudofStealth() const; -- bool
statbonuses:GetSkillAttackProc(int idx) const; -- int32
statbonuses:GetSkillDamageAmount(int idx) const; -- int32
statbonuses:GetSkillDamageAmount2(int idx) const; -- int32
statbonuses:GetSkillDmgTaken(int idx) const; -- int16
statbonuses:GetSkillProc(int idx) const; -- uint32
statbonuses:GetSkillProcSuccess(int idx) const; -- uint32
statbonuses:GetSkillReuseTime(int idx) const; -- int32
statbonuses:GetSlayUndead(int idx) const; -- int32
statbonuses:GetSongRange() const; -- int32
statbonuses:GetSpellCritDmgIncNoStack() const; -- int32
statbonuses:GetSpellCritDmgIncrease() const; -- int32
statbonuses:GetSpellDamageShield() const; -- int
statbonuses:GetSpellDmg() const; -- int32
statbonuses:GetSpellOnDeath(int idx) const; -- uint32
statbonuses:GetSpellOnKill(int idx) const; -- uint32
statbonuses:GetSpellProcChance() const; -- int32
statbonuses:GetSpellShield() const; -- int
statbonuses:GetSpellThresholdGuard(int idx) const; -- uint32
statbonuses:GetSpellTriggers(int idx) const; -- uint32
statbonuses:GetStrikeThrough() const; -- int32
statbonuses:GetStunBashChance() const; -- int8
statbonuses:GetStunResist() const; -- int32
statbonuses:GetTradeSkillMastery() const; -- uint8
statbonuses:GetTriggerMeleeThreshold() const; -- bool
statbonuses:GetTriggerOnValueAmount() const; -- bool
statbonuses:GetTriggerSpellThreshold() const; -- bool
statbonuses:GetTripleAttackChance() const; -- int32
statbonuses:GetTripleBackstab() const; -- uint8
statbonuses:GetTwoHandBluntBlock() const; -- int32
statbonuses:GetUnfailingDivinity() const; -- int32
statbonuses:GetVampirism() const; -- int32
statbonuses:GetVoiceGraft() const; -- uint32
statbonuses:GetWIS() const; -- int32
statbonuses:GetWISCapMod() const; -- int32
statbonuses:GetXPRateMod() const; -- int
statbonuses:GetbrassMod() const; -- uint32
statbonuses:Geteffective_casting_level() const; -- int
statbonuses:Getextra_xtargets() const; -- uint16
statbonuses:Gethaste() const; -- int32
statbonuses:Gethastetype2() const; -- int32
statbonuses:Gethastetype3() const; -- int32
statbonuses:Gethatemod() const; -- int8
statbonuses:Getinhibitmelee() const; -- int32
statbonuses:Getmovementspeed() const; -- int
statbonuses:GetpercussionMod() const; -- uint32
statbonuses:Getreflect_chance() const; -- int
statbonuses:GetsingingMod() const; -- uint32
statbonuses:Getskillmod(int idx) const; -- int32
statbonuses:Getskillmodmax(int idx) const; -- int32
statbonuses:GetsongModCap() const; -- uint32
statbonuses:GetstringedMod() const; -- uint32
statbonuses:GetwindMod() const; -- uint32
```

# Raid
```lua
raid:BalanceHP(int penalty, uint32 group_id); -- void
raid:CastGroupSpell(Lua_Mob caster, int spell_id, uint32 group_id); -- void
raid:GetClientByIndex(int index); -- Lua_Client
raid:GetGroup(Lua_Client c); -- uint32
raid:GetGroup(const char *c); -- uint32
raid:GetHighestLevel(); -- int
raid:GetID(); -- int
raid:GetLowestLevel(); -- int
raid:GetMember(int index); -- Lua_Client
raid:GetTotalRaidDamage(Lua_Mob other); -- uint32
raid:GroupCount(uint32 group_id); -- int
raid:IsGroupLeader(const char *name); -- bool
raid:IsLeader(Lua_Client c); -- bool
raid:IsLeader(const char *c); -- bool
raid:IsRaidMember(const char *name); -- bool
raid:RaidCount(); -- int
raid:SplitExp(uint32 exp, Lua_Mob other); -- void
raid:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
raid:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, Lua_Client splitter); -- void
raid:TeleportGroup(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h, uint32 group_id); -- void
raid:TeleportRaid(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h); -- void
```

#  Lua General Functions
```lua
eq.active_speak_activity(int task_id); -- int
eq.active_speak_task(); -- int
eq.active_tasks_in_set(int task_set); -- int
eq.add_area(int id, int type, float min_x, float max_x, float min_y, float max_y, float min_z, float max_z); -- void
eq.assign_group_to_instance(uint32 instance_id); -- void
eq.assign_raid_to_instance(uint32 instance_id); -- void
eq.assign_task(int task_id); -- void
eq.assign_to_instance(uint32 instance_id); -- void
eq.attack(const char *client_name); -- void
eq.attack_npc(int entity_id); -- void
eq.attack_npc_type(int npc_type); -- void
eq.bury_player_corpse(uint32 char_id); -- bool
eq.check_title(uint32 title_set); -- void
eq.clear_areas(); -- void
eq.clear_npctype_cache(int npctype_id); -- void
eq.clear_opcode(int op); -- void
eq.clear_proximity(); -- void
eq.clear_spawn_timers(); -- void
eq.clock(); -- double
eq.collect_items(uint32 item_id, bool remove); -- int
eq.completed_tasks_in_set(int task_set); -- int
eq.create_door(const char *model, float x, float y, float z, float h, int open_type, int size); -- void
eq.create_ground_object(uint32 item_id, float x, float y, float z, float h); -- void
eq.create_ground_object(uint32 item_id, float x, float y, float z, float h, uint32 decay_time); -- void
eq.create_ground_object_from_model(const char *model, float x, float y, float z, float h); -- void
eq.create_ground_object_from_model(const char *model, float x, float y, float z, float h, int type); -- void
eq.create_ground_object_from_model(const char *model, float x, float y, float z, float h, int type, uint32 decay_time); -- void
eq.create_guild(const char *name, const char *leader); -- void
eq.create_instance(const char *zone, uint32 version, uint32 duration); -- uint32
eq.cross_zone_message_player_by_name(uint32 type, const char *player, const char *message); -- void
eq.cross_zone_set_entity_variable_by_client_name(const char *player, const char *id, const char *m_var); -- void
eq.cross_zone_signal_client_by_char_id(uint32 player_id, int signal); -- void
eq.cross_zone_signal_client_by_name(const char *player, int signal); -- void
eq.debug(std::string message); -- void
eq.debug(std::string message, int level); -- void
eq.delete_global(const char *name); -- void
eq.depop(); -- void
eq.depop(int npc_type); -- void
eq.depop_all(); -- void
eq.depop_all(int npc_type); -- void
eq.depop_with_timer(); -- void
eq.depop_with_timer(int npc_type); -- void
eq.depop_zone(bool start_spawn_status); -- void
eq.destroy_instance(uint32 instance_id); -- void
eq.disable_proximity_say(); -- void
eq.disable_recipe(uint32 recipe_id); -- bool
eq.disable_spawn2(int spawn2_id); -- void
eq.enable_proximity_say(); -- void
eq.enable_recipe(uint32 recipe_id); -- bool
eq.enable_spawn2(int spawn2_id); -- void
eq.enable_title(uint32 title_set); -- void
eq.enabled_task_count(int task_set); -- int
eq.faction_value(); -- int
eq.fail_task(int task_id); -- void
eq.first_task_in_set(int task_set); -- int
eq.flag_instance_by_group_leader(uint32 zone, uint32 version); -- void
eq.flag_instance_by_raid_leader(uint32 zone, uint32 version); -- void
eq.fly_mode(int flymode); -- void
eq.follow(int entity_id); -- void
eq.follow(int entity_id, int distance); -- void
eq.get_encounter(); -- std::string
eq.get_entity_list(); -- Lua_EntityList
eq.get_initiator(); -- Lua_Client
eq.get_instance_id(const char *zone, uint32 version); -- int
eq.get_instance_timer(); -- uint32
eq.get_instance_timer_by_id(uint16 instance_id); -- uint32
eq.get_level(int type); -- int
eq.get_owner(); -- Lua_Mob
eq.get_player_buried_corpse_count(uint32 char_id); -- int
eq.get_quest_item(); -- Lua_ItemInst
eq.get_spawn_condition(const char *zone, uint32 instance_id, int condition_id); -- int
eq.get_task_activity_done_count(int task, int activity); -- int
eq.get_zone_id(); -- int
eq.get_zone_instance_id(); -- int
eq.get_zone_instance_version(); -- int
eq.get_zone_weather(); -- int
eq.is_disc_tome(int item_id); -- bool
eq.is_paused_timer(const char *timer); -- bool
eq.is_task_active(int task); -- bool
eq.is_task_activity_active(int task, int activity); -- bool
eq.is_task_appropriate(int task); -- bool
eq.is_task_completed(int task_id); -- int
eq.is_task_enabled(int task); -- bool
eq.item_link(int item_id); -- std::string
eq.last_task_in_set(int task_set); -- int
eq.map_opcodes(); -- void
eq.merchant_count_item(uint32 npc_id, uint32 item_id); -- int
eq.merchant_set_item(uint32 npc_id, uint32 item_id); -- void
eq.merchant_set_item(uint32 npc_id, uint32 item_id, uint32 quantity); -- void
eq.modify_npc_stat(const char *id, const char *value); -- void
eq.move_to(float x, float y, float z); -- void
eq.move_to(float x, float y, float z, float h); -- void
eq.move_to(float x, float y, float z, float h, bool save_guard_spot); -- void
eq.next_task_in_set(int task_set, int task_id); -- int
eq.path_resume(); -- void
eq.pause(int duration); -- void
eq.pause_timer(const char *timer); -- void
eq.popup(const char *title, const char *text, uint32 id, uint32 buttons, uint32 duration); -- void
eq.rain(int weather); -- void
eq.reloadzonestaticdata(); -- void
eq.remove_all_from_instance(uint32 instance_id); -- void
eq.remove_area(int id); -- void
eq.remove_from_instance(uint32 instance_id); -- void
eq.remove_spawn_point(uint32 spawn2_id); -- void
eq.remove_title(uint32 title_set); -- void
eq.repop_zone(); -- void
eq.reset_task_activity(int task, int activity); -- void
eq.respawn(int npc_type, int grid); -- void
eq.resume_timer(const char *timer); -- void
eq.safe_move(); -- void
eq.say_link(const char *phrase); -- std::string
eq.say_link(const char *phrase, bool silent); -- std::string
eq.say_link(const char *phrase, bool silent, const char *link_name); -- std::string
eq.scribe_spells(int max); -- int
eq.scribe_spells(int max, int min); -- int
eq.send_mail(const char *to, const char *from, const char *subject, const char *message); -- void
eq.set_anim(int npc_type, int anim_num); -- void
eq.set_global(const char *name, const char *value, int options, const char *duration); -- void
eq.set_guild(int guild_id, int rank); -- void
eq.set_next_hp_event(int hp); -- void
eq.set_next_inc_hp_event(int hp); -- void
eq.set_proximity(float min_x, float max_x, float min_y, float max_y); -- void
eq.set_proximity(float min_x, float max_x, float min_y, float max_y, float min_z, float max_z); -- void
eq.set_proximity(float min_x, float max_x, float min_y, float max_y, float min_z, float max_z, bool say); -- void
eq.set_sky(int sky); -- void
eq.set_time(int hour, int min); -- void
eq.set_time(int hour, int min, bool update_world); -- void
eq.set_timer(const char *timer, int time_ms); -- void
eq.set_timer(const char *timer, int time_ms, Lua_Encounter enc); -- void
eq.set_timer(const char *timer, int time_ms, Lua_ItemInst inst); -- void
eq.set_timer(const char *timer, int time_ms, Lua_Mob mob); -- void
eq.signal(int npc_id, int signal_id); -- void
eq.signal(int npc_id, int signal_id, int wait); -- void
eq.snow(int weather); -- void
eq.spawn2(int npc_type, int grid, int unused, double x, double y, double z, double heading); -- Lua_Mob
eq.spawn_condition(const char *zone, uint32 instance_id, int condition_id, int value); -- void
eq.spawn_from_spawn2(uint32 spawn2_id); -- Lua_Mob
eq.start(int wp); -- void
eq.stop(); -- void
eq.stop_all_timers(); -- void
eq.stop_all_timers(Lua_Encounter enc); -- void
eq.stop_all_timers(Lua_ItemInst inst); -- void
eq.stop_all_timers(Lua_Mob mob); -- void
eq.stop_follow(); -- void
eq.stop_timer(const char *timer); -- void
eq.stop_timer(const char *timer, Lua_Encounter enc); -- void
eq.stop_timer(const char *timer, Lua_ItemInst inst); -- void
eq.stop_timer(const char *timer, Lua_Mob mob); -- void
eq.summon_all_player_corpses(uint32 char_id, float x, float y, float z, float h); -- void
eq.summon_buried_player_corpse(uint32 char_id, float x, float y, float z, float h); -- void
eq.target_global(const char *name, const char *value, const char *duration, int npc_id, int char_id, int zone_id); -- void
eq.task_explored_area(int explore_id); -- void
eq.task_set_selector(int task_set); -- void
eq.task_time_left(int task_id); -- int
eq.toggle_spawn_event(int event_id, bool enable, bool strict, bool reset); -- void
eq.train_discs(int max); -- int
eq.train_discs(int max, int min); -- int
eq.unique_spawn(int npc_type, int grid, int unused, double x, double y, double z, double heading = 0.0); -- Lua_Mob
eq.update_instance_timer(uint16 instance_id, uint32 new_duration); -- void
eq.update_spawn_timer(uint32 id, uint32 new_time); -- void
eq.update_task_activity(int task, int activity, int count); -- void
eq.update_zone_header(std::string type, std::string value); -- void
eq.voice_tell(const char *str, uint32 macro_num, uint32 race_num, uint32 gender_num); -- void
eq.wear_change(uint32 slot, uint32 texture); -- void
eq.world_emote(int type, const char *str); -- void
eq.world_wide_marquee(uint32 type, uint32 priority, uint32 fadein, uint32 fadeout, uint32 duration, const char *message); -- void
eq.zone_emote(int type, const char *str); -- void
```

# ItemInst
```lua
iteminst:AddExp(uint32 exp); -- void
iteminst:ClearTimers(); -- void
iteminst:Clone(); -- Lua_ItemInst
iteminst:DeleteCustomData(std::string identifier); -- void
iteminst:GetAugment(int slot); -- Lua_ItemInst
iteminst:GetAugmentItemID(int slot); -- uint32
iteminst:GetAugmentType(); -- int
iteminst:GetCharges(); -- int
iteminst:GetColor(); -- uint32
iteminst:GetCustomData(std::string identifier); -- std::string
iteminst:GetCustomDataString(); -- std::string
iteminst:GetExp(); -- uint32
iteminst:GetID(); -- uint32
iteminst:GetItem(); -- Lua_Item
iteminst:GetItem(int slot); -- Lua_ItemInst
iteminst:GetItemID(int slot); -- uint32
iteminst:GetItemScriptID(); -- uint32
iteminst:GetKillsNeeded(int current_level); -- uint32
iteminst:GetMaxEvolveLvl(); -- int
iteminst:GetPrice(); -- uint32
iteminst:GetTotalItemCount(); -- int
iteminst:GetUnscaledItem(int slot); -- Lua_Item
iteminst:IsAmmo(); -- bool
iteminst:IsAugmentable(); -- bool
iteminst:IsAugmented(); -- bool
iteminst:IsEquipable(int race, int class_); -- bool
iteminst:IsEquipable(int slot_id); -- bool
iteminst:IsExpendable(); -- bool
iteminst:IsInstNoDrop(); -- bool
iteminst:IsStackable(); -- bool
iteminst:IsType(int item_class); -- bool
iteminst:IsWeapon(); -- bool
iteminst:Lua_ItemInst(const Lua_ItemInst& o); -- Lua_ItemInst::Lua_ItemInst(const
iteminst:SetCharges(int charges); -- void
iteminst:SetColor(uint32 color); -- void
iteminst:SetCustomData(std::string identifier, bool value); -- void
iteminst:SetCustomData(std::string identifier, float value); -- void
iteminst:SetCustomData(std::string identifier, int value); -- void
iteminst:SetCustomData(std::string identifier, std::string value); -- void
iteminst:SetExp(uint32 exp); -- void
iteminst:SetInstNoDrop(bool flag); -- void
iteminst:SetPrice(uint32 price); -- void
iteminst:SetScale(double scale_factor); -- void
iteminst:SetScaling(bool v); -- void
iteminst:SetTimer(std::string name, uint32 time); -- void
iteminst:StopTimer(std::string name); -- void
iteminst:operator=(const Lua_ItemInst& o); -- Lua_ItemInst&
```

# Corpse
```lua
corpse:AddItem(uint32 itemnum, uint16 charges, int16 slot, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5); -- void
corpse:AddLooter(Lua_Mob who); -- void
corpse:AllowMobLoot(Lua_Mob them, uint8 slot); -- void
corpse:Bury(); -- void
corpse:CanMobLoot(int charid); -- bool
corpse:CountItems(); -- uint32
corpse:Delete(); -- void
corpse:Depop(); -- void
corpse:GetCharID(); -- uint32
corpse:GetCopper(); -- uint32
corpse:GetDBID(); -- uint32
corpse:GetDecayTime(); -- uint32
corpse:GetGold(); -- uint32
corpse:GetPlatinum(); -- uint32
corpse:GetSilver(); -- uint32
corpse:GetWornItem(int16 equipSlot); -- uint32
corpse:IsEmpty(); -- bool
corpse:IsLocked(); -- bool
corpse:IsRezzed(); -- bool
corpse:Lock(); -- void
corpse:RemoveCash(); -- void
corpse:RemoveItem(uint16 lootslot); -- void
corpse:ResetLooter(); -- void
corpse:Save(); -- bool
corpse:SetCash(uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
corpse:SetDecayTimer(uint32 decaytime); -- void
corpse:Summon(Lua_Client client, bool spell, bool checkdistance); -- bool
corpse:UnLock(); -- void
```

