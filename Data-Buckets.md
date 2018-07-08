### What are Data Buckets?

* Data buckets are a replacement to the well-known `qglobals`, but they are far more performant, reliable and simpler to use

* You can use data buckets to store values unique to anything you would like, for example
  * NPC based flags
  * Zone based flags
  * Character based flags 
  * etc.

# Functions

* Data buckets exist in these 3 main functions in both Perl and LUA

```
get_data(std::string bucket_key)
set_data(std::string bucket_key, std::string bucket_value, uint32 expires_at_unix = 0)
delete_data(std::string bucket_key)
```

# Storage

* Data buckets are stored in the [[data_buckets]] table and has a very simple structure
  * **id**
  * **key**
  * **value**
  * **expires**

* Expired data bucket rows will not be queryable via the quest API, they may exist in a table until 5-10 minutes have past and the server will garbage collect and wipe the table clean of expired buckets

# Usage Examples

### Perl

* In this simple example you can see that we are keying by character id to set the flag to make this unique per player, we are setting it with the value of 70, and since we didn't set the optional value of unix time it never expires

```perl
if ($text =~/character-flag-test/i) {
    $key = $client->CharacterID() . "-some-epic-flag";
    quest::set_data($key, 70);
    quest::say("You have traveled far! You have a mighty (" . quest::get_data($key) . ") epic points!");
}
```

![image](https://user-images.githubusercontent.com/3319450/42416821-8cef6690-823e-11e8-8b78-caec1a213f71.png)


### LUA

* In this example below you can see that we set a simple global flag, we immediately access it, delete it and then try to unsuccessfully access it again because the bucket data had already been deleted

```lua
if (e.message:findi("test")) then
    e.self:Say("This is a test!")
    eq.set_data("lua_test_key", "lua_value");
    e.self:Say("We just set some bucket data with '".. eq.get_data("lua_test_key") .. "'");
    eq.delete_data("lua_test_key");
    e.self:Say("I'm going to try and access the value again... '".. eq.get_data("lua_test_key") .. "'");
end
```

![image](https://user-images.githubusercontent.com/3319450/42416831-a726d71e-823e-11e8-92d5-cad58040e00c.png)

# Ways to Key Buckets

**By Character**

```
perl
$key   = $client->CharacterID() . "-some-flag";
$value = 70;
quest::set_data($key, $value);
```

**By Door (And Zone)**

```
perl

sub EVENT_CLICKDOOR {
    quest::say($doorid);
    if ($doorid == 4) {
        $key   = $zoneid . '-' . $client->CharacterID() . "-last-person-to-click-door";
        $value = $client->GetCleanName();

        if (quest::get_data($key)) {
            $client->Message(15, "You know... the last person to click this door was '" . quest::get_data($key) . "'");
        }

        quest::set_data($key, $value);
    }
}
```

**Result**

![image](https://user-images.githubusercontent.com/3319450/42416886-d2caadae-823f-11e8-9b49-a6bd21bf8f73.png)

**Database Result**

![image](https://user-images.githubusercontent.com/3319450/42416888-dfd7a966-823f-11e8-8fc6-1829ed0c35c3.png)
