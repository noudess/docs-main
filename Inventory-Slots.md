(This page is out-of-date..update in progress)

## Server-recognized slots

### Equipment slots (worn)

*   slotCharm       = 0
*   slotEar1        = 1
*   slotHead        = 2
*   slotFace        = 3
*   slotEar2        = 4
*   slotNeck        = 5
*   slotShoulders   = 6
*   slotArms        = 7
*   slotBack        = 8
*   slotWrist1      = 9
*   slotWrist2      = 10
*   slotRange       = 11
*   slotHands       = 12
*   slotPrimary     = 13
*   slotSecondary   = 14
*   slotFinger1     = 15
*   slotFinger2     = 16
*   slotChest       = 17
*   slotLegs        = 18
*   slotFeet        = 19
*   slotWaist       = 20
*   slotPowerSource = 21
*   slotAmmo        = 22

### General slots (personal)

*   slotGeneral1  = 23
*   slotGeneral2  = 24
*   slotGeneral3  = 25
*   slotGeneral4  = 26
*   slotGeneral5  = 27
*   slotGeneral6  = 28
*   slotGeneral7  = 29
*   slotGeneral8  = 30
*   slotGeneral9  = 31
*   slotGeneral10 = 32

Bag slots in general inventory are:

*   slotGeneral1  : 251 -> 260
*   slotGeneral2  : 261 -> 270
*   slotGeneral3  : 271 -> 280
*   slotGeneral4  : 281 -> 290
*   slotGeneral5  : 291 -> 300
*   slotGeneral6  : 301 -> 310
*   slotGeneral7  : 311 -> 320
*   slotGeneral8  : 321 -> 330
*   slotGeneral9  : 331 -> 340
*   slotGeneral10 : 341 -> 350

### Cursor slot

*   slotCursor = 33

Bag slots in cursor inventory are:

*   slotCursor : 351 -> 360

### Tribute

Tribute items are slots 400->404, these items are not visible, but are counted for stats/effects.

### Bank

Bank slots are 2000 -> 2023

Bags in the bank are:

*   2000: 2031->2040
*   2001: 2041->2050
*   2002: 2051->2060
*   2003: 2061->2070
*   2004: 2071->2080
*   2005: 2081->2090
*   2006: 2091->2100
*   2007: 2101->2110
*   2008: 2111->2120
*   2009: 2121->2130
*   2010: 2131->2140
*   2011: 2141->2150
*   2012: 2151->2160
*   2013: 2161->2170
*   2014: 2171->2180
*   2015: 2181->2190
*   2016: 2191->2200
*   2017: 2201->2210
*   2018: 2211->2220
*   2019: 2221->2230
*   2020: 2231->2240
*   2021: 2241->2250
*   2022: 2251->2260
*   2023: 2261->2270

### Shared Bank

Shared bank slots are 2500 and 2501

Note: These are stored in the sharedbank table, not the inventory table.

Bags in the shared bank are:

*   2500: 2531->2540
*   2501: 2541->2550

#### SoF Slots

### Equipped slots

(somebody should make this prettier some day)

*   SLOT_CHARM= 0
*   SLOT_EAR01= 1
*   SLOT_HEAD= 2
*   SLOT_FACE= 3
*   SLOT_EAR02= 4
*   SLOT_NECK= 5
*   SLOT_SHOULDER= 6
*   SLOT_ARMS= 7
*   SLOT_BACK= 8
*   SLOT_BRACER01= 9
*   SLOT_BRACER02= 10
*   SLOT_RANGE= 11
*   SLOT_HANDS= 12
*   SLOT_PRIMARY= 13
*   SLOT_SECONDARY= 14
*   SLOT_RING01= 15
*   SLOT_RING02= 16
*   SLOT_CHEST= 17
*   SLOT_LEGS= 18
*   SLOT_FEET= 19
*   SLOT_WAIST= 20
*   SLOT_POWERSOURCE= 21
*   SLOT_AMMO= 22

### Inventory Slots

NOTE: Numbering for personal inventory goes top to bottom, then left to right

It's the opposite for inside bags: left to right, then top to bottom

Example:

inventory:containers:

*   1 51 2
*   2 63 4
*   3 75 6
*   4 87 8
*     9 10

### Personal Inventory

Personal inventory slots 23 through 30.

Bags in personal inventory are:

*   23: 262->271
*   24: 272->281
*   25: 282->291
*   26: 292->301
*   27: 302->311
*   28: 312->321
*   29: 322->331
*   30: 332->341

### Cursor

Cursor is slot 31, and the bag slots for the cursor are 342->351 (haven't confirmed slots inside bag on cursor for SoF yet).

### SoF Bank

Bank slots in SoF are 2000->2023

Bags in the bank are:

*   2000 2004 2008 2012 2016 2020
*   2001 2005 2009 2013 2017 2021
*   2002 2006 2010 2014 2018 2022
*   2003 2007 2011 2015 2019 2023

Slots inside those bags are:

Note: Other than the addition of the 8 new slots, the main bank slots are the same as Titanium, but slots inside bags are +1 to what Titanium uses.

*   2000 = 2032 - 2041
*   2001 = 2042 - 2051
*   2002 = 2052 - 2061
*   2003 = 2062 - 2071

*   2004 = 2072 - 2061
*   2005 = 2082 - 2091
*   2006 = 2092 - 2101
*   2007 = 2102 - 2111

*   2008 = 2112 - 2121
*   2009 = 2122 - 2131
*   2010 = 2132 - 2141
*   2011 = 2142 - 2151

*   2012 = 2152 - 2161
*   2013 = 2162 - 2171
*   2014 = 2172 - 2181
*   2015 = 2182 - 2191

*   8 New Bank Slots:
*   2016 = 2192 - 2201
*   2017 = 2202 - 2211
*   2018 = 2212 - 2221
*   2019 = 2222 - 2231

*   2020 = 2232 - 2241
*   2021 = 2242 - 2251
*   2022 = 2252 - 2261
*   2023 = 2262 - 2271

### SoF Shared Bank

Shared bank slots in SoF are 2500 and 2501

Note: These are the same as in Titanium, but the slots for inside bags are +1 to the ones in Titanium

Bags in the shared bank are:

*   2500 = 2532 - 2541
*   2501 = 2542 - 2551