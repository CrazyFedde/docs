# Release Notes

- [Versioning Scheme](#versioning-scheme)
- [Beta 0.x.x](#beta-0.x.x)

<a name="versioning-scheme"></a>
## Versioning Scheme

AvaIre follows the [Semantic Versioning](http://semver.org/) scheme, following the convention: `major.minor.patch`. Minor application releases represents new addtions, commands, features and reworks of the existing codebase. Patch releases represents bug fixes, refractoring of existing code and very minor changes that wont affect other things in the code base

Major releases are separated by many months or years and represent fundamental shifts in the applications's architecture and conventions.

<a name="beta-0.x.x"></a>
## Beta 0.x.x

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