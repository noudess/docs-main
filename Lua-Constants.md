There are several constant tables exported to Lua that represent constants from the server:

[Return to the Lua API](Lua-API)

InventoryWhere
```
{
	Integer Personal;
	Integer Bank;
	Integer SharedBank;
	Integer Trading;
	Integer Cursor;
}
```

Event
```
{
	Integer say;
	Integer trade;
	Integer death;
	Integer spawn;
	Integer combat;
	Integer slay;
	Integer waypoint_arrive;
	Integer waypoint_depart;
	Integer timer;
	Integer signal;
	Integer hp;
	Integer enter;
	Integer exit;
	Integer enter_zone;
	Integer click_door;
	Integer loot;
	Integer zone;
	Integer level_up;
	Integer killed_merit ;
	Integer cast_on;
	Integer task_accepted;
	Integer task_stage_complete;
	Integer task_update;
	Integer task_complete;
	Integer task_fail;
	Integer aggro_say;
	Integer player_pickup;
	Integer popup_response;
	Integer proximity_say;
	Integer cast;
	Integer cast_begin;
	Integer scale_calc;
	Integer item_enter_zone;
	Integer target_change;
	Integer hate_list;
	Integer spell_effect;
	Integer spell_buff_tic;
	Integer spell_fade;
	Integer spell_effect_translocate_complete;
	Integer combine_success ;
	Integer combine_failure ;
	Integer item_click;
	Integer item_click_cast;
	Integer group_change;
	Integer forage_success;
	Integer forage_failure;
	Integer fish_start;
	Integer fish_success;
	Integer fish_failure;
	Integer click_object;
	Integer discover_item;
	Integer disconnect;
	Integer connect;
	Integer item_tick;
	Integer duel_win;
	Integer duel_lose;
	Integer encounter_load;
	Integer encounter_unload;
	Integer command;
	Integer drop_item;
	Integer destroy_item;
	Integer feign_death;
	Integer weapon_proc;
	Integer equip_item;
	Integer unequip_item;
	Integer augment_item;
	Integer unaugment_item;
	Integer augment_insert;
	Integer augment_remove;
	Integer enter_area;
	Integer leave_area;
	Integer death_complete;
	Integer unhandled_opcode;
}
```

Faction
```
{
	Integer Ally;
	Integer Warmly;
	Integer Kindly;
	Integer Amiable;
	Integer Indifferent;
	Integer Apprehensive;
	Integer Dubious;
	Integer Threatenly;
	Integer Scowls;
}
```

Slot
```
{
	Integer Charm;
	Integer Ear1;
	Integer Head;
	Integer Face;
	Integer Ear2;
	Integer Neck;
	Integer Shoulder;
	Integer Arms;
	Integer Back;
	Integer Bracer1;
	Integer Bracer2;
	Integer Range;
	Integer Hands;
	Integer Primary;
	Integer Secondary;
	Integer Ring1;
	Integer Ring2;
	Integer Chest;
	Integer Legs;
	Integer Feet;
	Integer Waist;
	Integer Ammo;
	Integer PersonalBegin;
	Integer PersonalEnd;
	Integer Cursor;
	Integer CursorEnd;
	Integer Tradeskill;
	Integer Augment;
	Integer PowerSource;
	Integer Invalid;
}
```

Material
```
{
	Integer Head;
	Integer Chest;
	Integer Arms;
	Integer Bracer;
	Integer Hands;
	Integer Legs;
	Integer Feet;
	Integer Primary;
	Integer Secondary;
	Integer Max;
}
```

ClientVersion
```
{
	Integer Unknown;
	Integer 62;
	Integer Titanium;
	Integer SoF;
	Integer SoD;
	Integer Underfoot;
	Integer RoF;
}
```

Appearance
```
{
	Integer Standing;
	Integer Sitting;
	Integer Crouching;
	Integer Dead;
	Integer Looting;
}
```

SpecialAbility
```
{
	Integer summon;
	Integer enrage;
	Integer rampage;
	Integer area_rampage;
	Integer flurry;
	Integer triple_attack;
	Integer quad_attack;
	Integer innate_dual_wield;
	Integer bane_attack;
	Integer magical_attack;
	Integer ranged_attack;
	Integer unslowable;
	Integer unmezable;
	Integer uncharmable;
	Integer unstunable;
	Integer unsnareable;
	Integer unfearable;
	Integer undispellable;
	Integer immune_melee;
	Integer immune_magic;
	Integer immune_fleeing;
	Integer immune_melee_except_bane;
	Integer immune_melee_except_magical;
	Integer immune_aggro;
	Integer immune_aggro_on;
	Integer immune_casting_from_range;
	Integer immune_feign_death;
	Integer immune_taunt;
	Integer tunnelvision;
	Integer dont_buff_friends;
	Integer immune_pacify;
	Integer leash;
	Integer tether;
	Integer destructible_object;
	Integer no_harm_from_client;
}
```