## How to set a character to GM Status

1. Log in to your server with the character you wish to make a GM
2. Log out to the character selection screen.
3. Go into your SQL editor of choice (or command line) and change account.status to 255.
4. Log in and enjoy GM commands (typing #help will give you a list of commands)

For example, in linux step three would look something like this:

    $ mysql -u my_db_username -p
    mysql> use eqemu;
    mysql> UPDATE account SET status = 255 WHERE name = 'my_character_name';
    mysql> quit;

In this example, `my_db_username` is the username that you set for the mysql database during server installation and `my_character_name` is the name of the character you setting to GM status.

You may find the [[account]] table schema a useful reference as well.

## What can I do once I'm a GM?

For a list of commands you can use once you've elevated an account to GM status, see [[In Game Command Reference (Mostly GM's)]].  This reference can also be found in the table of contents on the right under Reference Lists.