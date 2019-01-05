# Getting Started

So you would like to understand spells?  It's a bit of a journey, so let's get started.

There are tens of thousands of records in your [spells_new](https://github.com/EQEmu/Server/wiki/spells_new) table, and making sense of them all can be a little daunting (at least at first).  

Each spell has MANY fields related to it--and you're probably wondering what all of these fields do. 

## Slots

The first concept is that many fields are related to each other.  We have commonly referred to these related fields as "Slots", and most understand the concept that slots are somehow related.  There are 12 of these slots available, and the values in your database determine what happens when the spell is cast.

It might be easiest to view in simplified table, rather than as a series of fields.  It will also be useful to disregard many of the fields so that we can focus on understanding the mechanics of the spell, before we try to understand all of the fields in the spells_new database table.  Below is a simplified table of the spell "Greater Healing", that has a default Spell ID of 15:

**Slot** | **Effect ID** | **Effect Base Value** | **Max** | **Formula** 
----- | ----- | ----- | ----- | ----- | 
1 | 0 | 140 | 300 | 7 
2 | 254 | 0 | 0 | 100 
3 | 254 | 0 | 0 | 100 
4 | 254 | 0 | 0 | 100 
5 | 254 | 0 | 0 | 100 
6 | 254 | 0 | 0 | 100 
7 | 254 | 0 | 0 | 100 
8 | 254 | 0 | 0 | 100 
9 | 254 | 0 | 0 | 100 
10 | 254 | 0 | 0 | 100 
11 | 254 | 0 | 0 | 100 
12 | 254 | 0 | 0 | 100 

This simplified table shows that Slot 1 is where all the action is in the Greater Healing spell.  Slots 2-12 in this case just have default values, as they are unused.  If you're looking in your database at your spells_new table, you will see that each header row from table above appears as a database field for each slot (IE effectid1, effectid2...effectid12; max1, max2...max12).

## Spell Effects

There is an entire page on the Wiki describing each [Spell Effect](https://github.com/EQEmu/Server/wiki/Spell-Effect-IDs).  A spell effect, in simplest terms, determines what is modified, or what is caused to happen, by the spell.  It is important to understand that each slot, as shown above, can have a Spell Effect enumerated in the Effect ID field--that is to say that each Spell can have one or more spell effects that occur when the spell is cast.

Dissecting the information presented in the Greater Healing spell table above, we see that Spell Effect 0 is listed in the first slot (effectid1 field in your database).  Cross-referencing with the Spell Effect list, we find that Spell Effect 0 is "SE_CurrentHP", or Spell Effect Current Hit Points.  We can therefore surmise the the Greater Healing spell must have something to do with hit points.  

## Base Values

Base Values are integers that are used in coordination with the Spell Effect to determine an outcome.  Each [Spell Effect](https://github.com/EQEmu/Server/wiki/Spell-Effect-IDs) does something slightly different with its base value, as demonstrated in the Spell Effects table.  

In the case of our Greater Healing spell, we see a Base Value of 140 in Slot 1 (effect_base_value1 field in your database).  Since we know the Spell Effect will impact Current Hit Points, and since 140 is a positive value (as opposed to -140, for instance), we can say that the Healing spell will increase current hitpoints by 140--it will heal (add), rather than damage (subtract) from our current hit points.

Something isn't quite adding up yet, however:  we know that as you level up, your healing power seems to increase.  This mechanic can be explained by examining some additional fields.

## Max Values

Max Values are integers that are also used in coordination with the Spell Effect to determine an outcome.  Each Spell Effect's Max Value can do something slightly different, as demonstrated in the Spell Effect table.  

In the case of our Greater Healing spell, we see a Max Value of 300 in Slot 1 (max1 field in your database).  This means that the most this spell will adjust Current Hit Points by, is 300.  This is indicated by "Max Amt" in the Max Value column of the Spell Effect table for SE_CurrentHP.  Instead, if "Max Level" were indicated for Max Value of this spell effect, we would surmise that the spell would continue to scale as the player character gained levels, with each new level adding to the amount of hit points that could be restored.

So we have established that the Greater Healing spell is capable of changing current hit points in the amount of 140 to a maximum amount of 300--but how does it scale as you increase in levels from the first level you get the spell, until you max out the effectiveness of the spell and are able to heal 300 hit points?

## Formula

Formula values are integers that are used in coordination with the Spell Effect to determine its outcome as well.  Each Spell Effect can use a different formula, and those are found in the [spell_effects.cpp](https://github.com/EQEmu/Server/blob/master/zone/spell_effects.cpp) source file.  

In the case of our Greater Healing spell, we see that the value for Formula in Slot 1 is 7 (formula1 field in your database).  Referencing the source, we find that the spell calc is Base Value + User Level * Formula.  If we assume that we are a level 20 Cleric, casting the Greater Healing spell:  140 + 20 * 7 = 280.  This of course assumes that there are no focus effects being taken into consideration.  If we are instead a level 29 Druid, we would hit the spell's max value:  140 + 29 * 7 = 343--which is greater than the 300 hit point Max Value.  As a result, the Druid would only heal 300 hit points using this spell.

## Summary

It's important to understand the concept that at least one [Spell Effect](https://github.com/EQEmu/Server/wiki/Spell-Effect-IDs) is in use for each spell.  Each spell effect has a number of parameters that may behave differently from one spell effect to the next, even though they occupy the same field in the database--pay close attention to the Base Value, Limit Value, and Max Value for the Spell Effect, as they can drastically change the behavior of a spell.  