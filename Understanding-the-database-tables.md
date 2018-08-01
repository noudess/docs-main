# The following tables make up the faction capability.

The first three tables relate to establishing game factions, and how each faction responds to player characters.

## faction_list

The faction_list table contains one entry for each unique faction on the server.  The ID field identifies an in-game faction, but IS NOT directly associated with an NPC.  This list simply lists the in game factions and the starting value that all characters start at with this faction before they begin earning or losing faction.  DO NOT use these values in npc_types.  See npc_faction below for details.

## faction_list_mod

This table stores the static data that indicates what bonuses or penalties race, class and deity have on various factions.  For example, a character's standing may be worse with some factions due to that faction hating your deity.  Or like in the case of the Kerran race, they dislike Erudites.  These adjustments, combined with the starting value for everyone taken from faction_list, make up where you start in relation to all of the factions on Norrath.

## faction_values

This table stores the ever-changing data in regards to each characters actions in the game.  A running sum of all of the hit and gains in faction for characters is stored here, one line per char/faction pair.   Lines only exist if a character has at least one hit or credit based on in game actions.

These two tables are more about assigning each NPC a primary faction, while also establishing sister factions (assist worthy), enemy factions (attack worthy), and the hit taken by any PC that were to kill the PC.

## npc_faction

The ID from this table is where an NPC gets its entire faction behavior.  The ID assigned here, ties an NPC to their primary faction (from faction_list) as well as determines whether not not they will assist their primary faction comrades in battle.

But more than this, it serves as a key into the npc_faction_entries table. 

## npc_faction_entries

The npc_faction_entries table has two major roles.  First, entries are placed here that indicate how much faction is gained/lost with various factions if any NPC has this npc_faction_id is killed.  The second, is that you can list how these NPCS react to other NPCS of various other factions.

This table collects too much data in one place, and really should be broken down.  As it stands right now, if there are 10 different mobs that yield different faction hits when killed, there needs to be 10 different npc_factions and copies of their behavior records in new npc_faction_entries records.  If we separated out the hits into a separate table, then we would only need one copy of the behavior records.  We'll mark this as potential improvement. (In my work matching live faction data, it has required a ton of redundancy).