# Quest Globals to Data Buckets: How-To

* As many may know, Quest Globals are stored using a name, type, value, and duration.

* Due to this we can do a 1:1 conversion of all 8 types of globals:

* Types of Globals and their specificities: https://pastebin.com/kfUjyET4

# Conversion

* The way we will be storing this data is by using the bucket's name.

* As you can see, types 0 through six have similar names, based on NPC/Player/Zone specificity.
Type 7 is global, so the bucket name is just the qglobal name with no specificity.

* conversion.sql: https://pastebin.com/ecepEXU3

# Lua/Perl Requirements

* The Lua module necessary for using the Lua script (lua_modules/buckets.lua): https://pastebin.com/pTgDqFDL

* The Perl plugin necessary for using the Perl script (plugins/buckets.pl): https://pastebin.com/mhRvZC5x

# Lua/Perl Examples

* A Perl example of setting, reading, and deleting this version of data buckets: https://pastebin.com/9M5imeRH

* A Lua example of setting, reading, and deleting this version of data buckets: https://pastebin.com/vNP4dVSd