# Release Notes

- [Versioning Scheme](#versioning-scheme)
- [Beta 0.x.x](#beta-0.x.x)

<a name="versioning-scheme"></a>
## Versioning Scheme

AvaIre follows the [Semantic Versioning](http://semver.org/) scheme, following the convention: `major.minor.patch`. Minor application releases represents new addtions, commands, features and reworks of the existing codebase. Patch releases represents bug fixes, refractoring of existing code and very minor changes that wont affect other things in the code base

Major releases are separated by many months or years and represent fundamental shifts in the applications's architecture and conventions.

<a name="beta-0.x.x"></a>
## Beta 0.x.x

<a name="beta-0.42.x"></a>
### 0.42.x

#### New Features

 - Server Types
    - Each server can now be associated with a server-type, much like ranks, different server-types can give servers different or better perks.
 - Flexible Command Prefixes
    - Each server can now change the prefix any module uses on a per-server basis, the help command will also reflect those changes.
 - Customizable Music Playlists
    - Each server can now create their own set of music playlists that can be loaded into the music queue at any time.
 - Default Tag Message
    - If you tag the bot with no message added to it, the bot will now show some helpfull information about how to use the bot.
 - A bunch of new Commands, like:
    - [Fun - Dog, because dogs needs love too](/docs/commands#randomdog)
    - [Fun - XKCD Comcis](/docs/commands#xkcd)
    - [Fun - GFYCat Images](/docs/commands#gfycat)
    - [Fun - Dice Rolling](/docs/commands#dice)
    - [Fun - Chuck Norris Facts & Jokes](/docs/commands#chucknorris)
    - [Fun - Urban Dictionary](/docs/commands#urbandictionary)
    - [Muisc - Move Here](/docs/commands#movehere)
    - [Music - Playlist](/docs/commands#playlist)
    - [Music - Flush Queue](/docs/commands#flushqueue)
    - [Utility - URL Shortener](/docs/commands#shortenurl)
    - [Utility - URL Expander](/docs/commands#expandurl)
    - [System - Safe Reboot](/docs/commands#safereboot)

#### Changes

 - **Remove server check in the userinfo command for the bot**
    - If the userinfo command is used on the bot, the command will no longer show how many servers it is in, instead it will just show a neat little message.
 - **Limit music to channels the bot can speak in**
    - The bot will no longer attempt move to a voice channel it can't connect to or talk in.
 - **Help command now hints at shorthand usage**
    - When using any of the help command, a little hint will now be displayed alongside it, letting the user know they can use the command in other ways too.
 - **Remove RNG from Change Game Job**
    - The change game job will now always select an item from the config playing field, it now also supports some placeholders.
 - **Cleaner "Missing Permissions" messages**
    - All permission nodes now has a name attached to them in a language file, this will help give a clear message of what is missing or going wrong.
 - **Music puase inactivity checker**
    - Music that has been paused for too long will now be droped, this should help prevent any lingering voice connections from never droping.
 - **Song queue position**
    - The songs queue position is now sent along with the "song-added" message when a song is added to the queue.
 - **Role checks has been extract to the middleware level**
    - All role checks has now been extracted out to the middleware level, as a developer this should make it easier to customize who can run what commands.

#### Bug Fixes

 - Fix all outgoing messages to actually go through Envoyer.
 - Fix music unpausing unintentionally when a user joins voice.
 - Fix reloading events correctly.
 - Fix queue command somtimes sending empty messages.
 - Fix system module commands after command prefix changes.
 - Fix join and leave messages not working.
 - Fix Discord Bot Stats Update Job sending service requests correctly.
 - Fix checking for the propper guild type in guild join and leave events.
 - Fix playlist transformers parsing songs as null.
 - Fix YouTube playlist expiry date issue for storing songs.

#### The Rest

There have been a bunch of other minor changes made between the [0.33.x](#beta-0.33.x) and [0.42.x](#beta-0.42.x) updates, you can find all the changes in the [commits log](https://github.com/AvaIre/AvaIre/commits/master) on [github](https://github.com/AvaIre/AvaIre).

<a name="beta-0.33.x"></a>
### 0.33.x

#### New Features

 - Global Bot Blacklist
    - The global bot blacklist prevents any user on it from interacting with the bot, users can be added or removed from the list by bot admins using the new `;bla` and `;blr` commands.
 - Sharding Functionality
    - The bot instance can now be started in a sharded mode, this enables supports for 2500+ servers.
 - Reminder Command

#### Changes

 - **Rebrand music playlist to music queue.**
    - The playlist command has been renamed from `!playlist` to `!queue` since the playlist command will be used later for adding more features to the music.
 - **Removed the hyphen requirement for the help command.**
    - Prior to this change listing commands within a module named `test` would require the user to prefix their message with a hyphen(-), this is no longer required and can now be called just using `.help test` and the help command will notice that the first argument doesn't start with any command prefix and therefor assume it is a module.
 - **Convert all outgoing messages to go through Envoyer.**
    - All messages sent by the bot is sent through Envoyer, this means that it will be easier to change the entire messaging system in one go.
 - **Prettify command contents in the console**
    - All messages logged to the console and log-based-files will now go through a "prettifier" method that helps make the content look better in the console.
 - **Update and add more Join and Leave message placeholders.**
    - The `welcome` and `gooodbye` modules now has more placeholders, and all placeholders have been converted to using regex, allowing multiple uses of the same placeholder in one message.

#### Bug Fixes

 - Fix private message state being parsed correctly for language strings.
 - Fix checking for `IMessage` message object types for language strings.
 - Fix handeling missing permissions exceptions in Envoyer.
 - Fix music now-playing showing the currect user.
 - Fix dropping unused/inactive music connections.
 - Fix loading all users before sending login message.
 - Fix default placeholder messages for the `welcome` and `goodbye` modules.
 - Fix README documentation progress.

#### The Rest

There have been a bunch of other minor changes made between the [0.29.x](#beta-0.29.x) and [0.33.x](#beta-0.33.x) updates, you can find all the changes in the [commits log](https://github.com/AvaIre/AvaIre/commits/master) on [github](https://github.com/AvaIre/AvaIre).

<a name="beta-0.29.x"></a>
### 0.29.x

#### Slowmode command & functionality

Users with the **general.manage_server** permission can now enable or disable slowmode on a per-channel basis.