# Adding New Required Schema Migrations

* It's extremely simple
* When you add your .sql file, you still will add it as traditionally
    to our regular path
  * `utils/sql/git/required` - [Github Link](https://github.com/EQEmu/Server/tree/master/utils/sql/git/required)

# Changes in the Source

* You need to increment a define in the source that dictates what database version the source SHOULD be running at
  * Located in `common/version.h`

The database version will need to match the manifest entry you have added, more on that in a moment

`CURRENT_BINARY_DATABASE_VERSION = 9058`

# Conditions

```# Upgrade conditions:
# 	This won't be needed after this system is implemented, but it is used database that are not
#	yet using the versioning system to figure out where the database is schema wise to determine
#	which updates are necessary to run
#
# Example: Version|Filename.sql|Query_to_Check_Condition_For_Needed_Update|match type|text to match
#	0 = Database Version
#	1 = Filename.sql
#	2 = Query_to_Check_Condition_For_Needed_Update
#	3 = Match Type - If condition from match type to Value 4 is true, update will flag for needing to be ran
#		contains = If query results contains text from 4th value
#		match = If query results matches text from 4th value
#		missing = If query result is missing text from 4th value
#		empty = If the query results in no results
#		not_empty = If the query is not empty
#	4 = Text to match```

# The Manifest

* The manifest is stored always on Github and contains all the definitions and logic for determining if a database needs to update
  * `utils/sql/db_update_manifest.txt`
  * [Manifest Link](https://github.com/EQEmu/Server/blob/master/utils/sql/db_update_manifest.txt)

Add a line to the bottom of the file, it is going to look similar to the following

```
9058|2014_11_17_example_update_file.sql|SHOW TABLES LIKE 'character_mercenaries'|empty|
```

* This example would then have users run `2014_11_17_example_update_file.sql` when they don't have the 'character_mercenaries' table because of the empty condition

* That's it! As far as what is needed from a developer to have the server run the migration, that is all you need to do

# Other Manifest Examples:

### Example 1 (Missing):

```
9056|2014_11_08_RaidMembers.sql|SHOW COLUMNS FROM `raid_members` LIKE 'groupid'|missing|unsigned
```
