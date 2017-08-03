# Commands

- [Help Command](#help)
- [Administration](#administration)
- [Fun](#fun)
- [Music](#music)
- [Search](#search)
- [System](#system)
- [Utility](#utility)

<a name="introduction"></a>
## Introduction

This is the command reference for AvaIre. You can find more elaboration on each of the commands currently implemented here.

If you need for any further info, you can use the [help command](#help) for the bot to get info about command throttling limits, permission requirements and so forth. Got any questions? Check out #support in [AvaIre Central](#).

<a name="HelpCommand"></a>
## Help Command

Displays a list of available modules, commands in a given module, or information about a specific command.

#### Listing all modules

Using the help command with no additional arguments will display a list of all the modules.

    .help

#### Listing commands in module

Listing all commands in a module can be done by using the help command followed by the name of the module.

    .help <module>

> {tip} It is not required to type out the full name of the module, just typing a few characters will still list the commands in the module that starts with the given characters.<br>For example listing all the commands in the `Administration` module can be done by doing `.help a` for short.

#### Listing command information

Displaying a given command's information can be done by using `help` followed by the command you want to get information about.

    .help <command>

> {tip} Command aliases can be used as well, for example `.help .sid` will display help for the `.serverid` command.

<a name="administration"></a>
## Administration

All commands in the _Administration_ module uses the `.` prefix.

<a name="AiCommand"></a>
### AI

Toggles the AI module on or off for the current channel. If the module is enabled, users can tag the bot followed by a message or question and the bot will try and use its AI to process the message. By default AI messages will be enabled for all channels.

The **general.manage_server** permission is required to run this command.

<a name="AliasCommand"></a>
### Alias

Creates and maps a custom aliases for a pre-existing command. If an alias that already exists is given with no additional command the alias will be unbound.

The **general.manage_server** permission is required to run this command.

#### Usage

    .alias <alias trigger> [command to bind to]

#### Aliases

    .cmdmap

<a name="AliasesCommand"></a>
### Aliases

Lists all the existing command aliases and what they're bound to.

The **general.manage_server** permission is required to run this command.

#### Usage

    .aliases [page]

#### Aliases

    .aliaslist

<a name="BanCommand"></a>
### Ban

Bans the mentioned user from the server with the provided reason, all messages the user has sent in the last 7 days will also be deleted in the process.

The **general.ban_members** permission is required to run this command.

> This action will be reported to any channel that has [modlogging](#modlog) enabled on the server.

#### Usage

    .ban <user> [reason]

<a name="ChangePrefixCommand"></a>
### Change Prefix

Sets the prefix that should be used for all commands in a given module. If no prefix is provided the module's prefix will be reset to the default.

The following modules can be affected by this command.

 - [Administration](#administration)
 - [Fun](#fun)
 - [Help](#help)
 - [Music](#music)
 - [Search](#search)
 - [System](#system)
 - [Utility](#utility)

The **general.administrator** permission is required to run this command.

> {tip} It is not required to type out the full name of the module, just typing a few characters will get the module that starts with the given characters.<br>For example changing the prefix all the commands in the `Administration` module can be done by doing `.changeprefix a [prefix]` for short.

#### Usage

    .changeprefix <module> [prefix]

#### Aliases

    .avaireprefix

#### Tag Example

    @AvaIre prefix <module> [prefix]

<a name="ChannelCommand"></a>
### Channel

Displays what modules are enabled and disabled for the current channel, as-well as their settings if they're enabled. The following list of commands can change the behavior of the channel command:

 - [.ai](#AiCommand)
 - [.goodbye](#GoodbyeCommand)
 - [.goodbyemessage](#GoodbyeMessageCommand)
 - [.modlog](#ModlogCommand)
 - [.slowmode](#SlowmodeCommand)
 - [.welcome](#WelcomeCommand)
 - [.welcomemessage](#WelcomeMessageCommand)

#### Usage

    .channel

#### Aliases

    .chl

<a name="GoodbyeCommand"></a>
### Goodbye

Toggles the goodbye module on or off for the current channel. When the goodbye module is enabled, a message will be sent in the channel every time someone leaves the server.

The **general.manage_server** permission is required to run this command.

#### Usage

    .goodbye

#### Aliases

    .bye

<a name="GoodbyeMessageCommand"></a>
### Goodbye Message

Sets the goodbye message to the given string. If no arguments are passed, the goodbye message will be set back to the default goodbye message. You can customize how the goodbye message looks using [placeholders](/docs/{{version}}/placeholders).

The **general.manage_server** permission is required to run this command.

#### Usage

    .goodbyemessage [message]

#### Aliases

    .byemsg

<a name="KickCommand"></a>
### Kick

Kicks the mentioned user off the server with the provided reason.

The **general.kick_members** permission is required to run this command.

> This action will be reported to any channel that has [modlogging](#modlog) enabled on the server.

#### Usage

    .kick <user> [reason]

<a name="LanguageCommand"></a>
### Language

Displays the localization that is used on the server, you can also use this command to change the language that Ava will use when sending messages.

The **general.manage_server** permission is required to run this command.

#### Usage

    .language [local]

#### Aliases

    .lang

<a name="LevelCommand"></a>
### Level

Toggles the leveling system on or off for the current server. When the leveling system is enabled users will slowly accumulate XP from being active in the chat and using commands, every minute the user is active they will receive 10-15 XP.

The **general.manage_server** permission is required to run this command.

#### Usage

    .level

#### Aliases

    .lvl

<a name="LevelAlertsCommand"></a>
### Level Alerts

Toggles the level alerts system on or off for the current server. If a channel tag is passed as an argument, all level up alerts be sent in that channel. When the level alerts are enabled the bot will send a message each time a user levels up, letting them know they leveled up and what level they are now.

The **general.manage_server** permission is required to run this command.

#### Usage

    .levelalerts [channel]

#### Aliases

    .lvlalert

<a name="ModlogCommand"></a>
### Modlog

Toggles the modlog module on or off for the current channel. If the module is enabled, any action that will broadcast modlog messages([Ban](#ban), [Softban](#softban), [Kick](#kick)...) will be sent to this channel. By default modlogging will be disabled for all channels.

The **general.manage_server** permission is required to run this command.

#### Usage

    .modlog

#### Aliases

    .mlog

<a name="CommandModulesCommand"></a>
### Modules

Shows the status of all the command modules for the current channel and for the whole server if any commands are disabled globally. You can tag a channel if you want to see the command module status for the given channel.

The **general.administrator** permission is required to run this command.

#### Usage

    .modules [channel]

#### Aliases

    .module
    .mod

<a name="PurgeCommand"></a>
### Purge

Deletes up to 1,000 chat messages in any channel, you can pass a user mention as the second argument if you only want to delete messages sent by the mentioned user. Due to a restriction in the Discord API, the purge command will only work on messages sent in the last 14 days.

The **text.manage_messages** permission is required to run this command.

> {tip} Tagging a user will only delete any messages they have sent in the last `<amount>` of messages, for example `.purge 100 @JohnDoe#2854` will delete any messages the JohnDoe user has sent within the last 100 messages.

#### Usage

    .purge <amount> [tagged user]

#### Aliases

    .clear

<a name="ServerIdCommand"></a>
### Server ID

Displays ID of the server the command was ran in.

#### Usage

    .serverid

#### Aliases

    .sid

<a name="ServerInfoCommand"></a>
### Server Info

Displays information about the server the command was ran in. This includes the server's ID, owner, text and voice channels, members, roles, region, avatar and when it was created.

#### Usage

    .serverinfo

#### Aliases

    .sinfo

<a name="SetupCommand"></a>
### Setup

Helps setup different features within Ava for the current server.

The **general.administrator** permission is required to run this command.

#### Usage

    .setup [feature]

<a name="SlowmodeCommand"></a>
### Slowmode

Disables the slowmode module or enables it with the given settings, users with the **text.manage_messages** permission are exempt from slowmode limits. The slowmode module can be disabled by running the command with no arguments; if the `limit` and `decay` arguments are given the module will be enabled with the given settings.

The **general.manage_server** permission is required to run this command.

#### Usage

    .slowmode [limit] [decay]

<a name="SoftbanCommand"></a>
### Softban

Bans the mentioned user from the server with the provided reason. Any messages the user might've sent won't be deleted, if you want to force delete any old messages the user has sent see the [ban command](#ban).

The **text.ban_members** permission is required to run this command.

> This action will be reported to any channel that has [modlogging](#modlog) enabled on the server.

#### Usage

    .softban <user> [reason]

#### Aliases

    .sban

<a name="ToggleModuleCommand"></a>
### Toggle Module

Toggles the given command module on or off for the given channel, optionally for the whole server. When a command module is disabled no one can run any commands in the command module, you can disable commands on a per-channel basis by tagging the channel you want to affect.

The **general.administrator** permission is required to run this command.

> {tip} If you want to affect the whole server, you can completely omit the channel argument and just pass [on|off].

#### Usage

    .togglemodule <module> [channel|all] [on|off]

#### Aliases

    .tmod

<a name="UserIdCommand"></a>
### User ID

Displays ID of the user who ran the command or the ID of the tagged user.

#### Usage

    .userid [user]

#### Aliases

    .uid

<a name="UserInfoCommand"></a>
### User Info

Displays information about the user who ran the command or the tagged user. This includes the users username, ID, roles, the date they joined the server, the date they created their account, and how many servers they're in (That Ava knows about).

#### Usage

    .userinfo [user]

#### Aliases

    .uinfo

<a name="WelcomeCommand"></a>
### Welcome

Toggles the welcome module on or off for the current channel. When the welcome module is enabled, a message will be sent in the channel every time someone joins the server.

The **general.manage_server** permission is required to run this command.

#### Usage

    .welcome

#### Aliases

    .wel

<a name="WelcomeMessageCommand"></a>
### Welcome Message

Sets the welcome message to the given string. If no arguments are passed the welcome message will be set back to the default welcome message. You can customize how the welcome message looks using [placeholders](/docs/{{version}}/placeholders).

The **general.manage_server** permission is required to run this command.

#### Usage

    .welcomemessage [message]

#### Aliases

    .welmsg

<a name="fun"></a>
## Fun Commands

All commands in the _Fun_ module use the `>` prefix.

<a name="BlahCommand"></a>
### Blah

Blah?

#### Usage

    >blah

<a name="CanYouNotCommand"></a>
### CanYouNot

Can you not...?

#### Usage

    >canyounot

<a name="ChuckNorrisCommand"></a>
### Chuck Norris

Gets a random 100% true, real fact about Chuck Norris using the "Internet Chuck Norris Database".

#### Usage

    >chucknorris

#### Aliases

    >chuck
    >norris

<a name="CoinCommand"></a>
### Coin

Flips a coin for heads or tails.

#### Usage

    >coin

<a name="DiceCommand"></a>
### Dice

Rolls a set of dice, for example using `4d8` will roll four eight sided dice.

#### Usage

    >dice [D&D Dice]

<a name="HolidayCommand"></a>
### Holiday

Find out of today is a holyday.

#### Usage

    >holiday

<a name="LennyCommand"></a>
### Lenny

( ͡° ͜ʖ ͡°)

#### Usage

    >lenny

<a name="MemeCommand"></a>
### Meme

Creates a meme of the given type. Passing list as an argument sends a full list of memes that can be generated via the bot. You can also tag a user to use that user's avatar as a meme instead.

#### Usage

    >meme <meme|user|list> [top text] [bottom text]

<a name="RandomCatCommand"></a>
### Random Cat

Gets a random cat image from the internet.

#### Usage

    >randomcat

#### Aliases

    >cat

<a name="RandomDogCommand"></a>
### Random Dog

Gets a random dog image from the internet.

#### Usage

    >randomdog

#### Aliases

    >dog

<a name="RepeatCommand"></a>
### Repeat

Makes Ava repeat whatever you say.

#### Usage

    >repeat [message]

#### Aliases

    >echo

<a name="RipCommand"></a>
### RIP

Pay your respects.

#### Usage

    >rip

<a name="RollCommand"></a>
### Roll

Rolls a random number between 1 and 100, or between the numbers given.

#### Usage

    >roll [min] [max]

<a name="SayCommand"></a>
### Say

Makes Ava say whatever you want. If Ava has permissions to delete messages, the original message will be deleted and Ava's message will replace it.

#### Usage

    >say [message]

<a name="ShrugCommand"></a>
### Shrug

¯\\\_(ツ)\_/¯

#### Usage

    >shrug

<a name="SlowClapCommand"></a>
### Slowclap

Clap... Clap... Clap...

#### Usage

    >slowcap

<a name="music"></a>
## Music Commands

All commands in the _Music_ module use the `!` prefix.

<a name="FlushQueueCommand"></a>
### Flush Queue

Flushes the music queue, removing all songs currently waiting in the queue.

The **DJ** role is required to run this command.

#### Usage

    !flushqueue

#### Aliases

    !fqueue

<a name="RepeatMusicQueueCommand"></a>
### Repeat Music Queue

Toggles music looping on or off, the [queue](#queue) command be used to get the music looping status.

The **DJ** role is required to run this command.

#### Usage

    !repeatsongs

#### Aliases

    !repeat
    !loop

<a name="MoveHereCommand"></a>
### Move Here

Moves the bot into the same voice channel you're in. This command can be used to move the bot to a different voice channel while it's playing music without having the permissions to move other users. 

The **DJ** role is required to run this command.

#### Usage

    !movehere

#### Aliases

    !moveh

<a name="PauseCommand"></a>
### Pause

Pauses the song that is currently playing.

The **DJ** role is required to run this command.

#### Usage

    !pause

<a name="PlaylistCommand"></a>
### Playlist

Allows music DJs to create, list, update, and delete music playlists. This command has a bunch of sub-commands that are used to manage the playlists; to make it a bit easier, here are all the sub-commands.

 - [Add song to Playlist](#playlist-add)
 - [Create new Playlist](#playlist-create)
 - [Delete existing Playlist](#playlist-delete)
 - [Remove a song from an existing Playlist](#playlist-remove)
 - [Load Playlist into the Music queue](#playlist-load)
 - [List Songs in the Playlist](#playlist-list)
 - [Rename Playlist](#playlist-rename)

The **DJ** role is required to run this command.

#### Usage

    !playlist [name] [arguments]

#### Aliases

    !list
    !pl

<a name="playlist-add"></a>
### Playlist - Add a song to a playlist

Adds a song to the a existing playlist, if you don't already have playlist you can [create a new playlist](#playlist-create).

#### Usage

    !playlist <name> add <song url>

#### Aliases

    !playlist <name> a <song url>

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="playlist-create"></a>
### Playlist - Create new playlist

Creates a new playlist for the server with the given name. When the playlist has been created you can start [adding songs to it](#playlist-add), if you butchered the name you can [rename the playlist](#playlist-rename) without deleting all the songs in it.

#### Usage

    !playlist <name> create

#### Aliases

    !playlist <name> c

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="playlist-delete"></a>
### Playlist - Delete a playlist

Deletes a playlist and all the songs in it. **Keep in mind that deleting the playlist is a permanent action and can not be undone!** There is **NO** confirmation if you are sure that you want to delete it; the playlist will just be deleted if you use the command.

> {tip} If the playlist is loaded into the music queue when the playlist is deleted, the music will still continue to play all the way through.

#### Usage

    !playlist <name> delete

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="playlist-remove"></a>
### Playlist - Remove a song from an existing playlist 

Removes the song with the given ID for the current playlist if it's in queue.

#### Usage

    !playlist <name> removesong <ID>

#### Aliases

    !playlist <name> remove <ID>

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="playlist-load"></a>
### Playlist - Load a playlist into the queue

Loads the playlist into the music queue. If the bot is not already playing music this command will also connect the bot to the same voice channel you are in and initialize music playback. If the playlist is empty you can [add some songs](#playlist-add).

#### Usage

    !playlist <name> load

#### Aliases

    !playlist <name> play
    !playlist <name> l

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="playlist-list"></a>
### Playlist - List songs in the playlist

Lists the songs in the playlist with the given name. The response will be paginated to only show ten songs at a time; you can jump to different pages by passing a page number for the playlist as an additional argument. If you don't have any songs in the playlist you can [add songs](#playlist-add).

#### Usage

    !playlist <name> [page number]

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="playlist-rename"></a>
### Playlist - Rename a playlist

Rename an existing playlist. The string passed to the command will be used as the new name.

#### Usage

    !playlist <name> renameto <new name>

#### Aliases

    !playlist <name> rename <new name>
    !playlist <name> r <new name>

**You can replace the `!playlist` command with any of [playlist command aliases](#playlist).**

<a name="QueueCommand"></a>
### Queue

Returns the song that is playing right now and some attached information. This includes who requested it, how much of the song is left and the volume the song is playing at plus the rest of the songs currently in queue. If the **remove** argument and the ID of the song are passed to the command, the song with the given ID will be removed from the music queue.

#### Usage

    !queue [remove] [ID]

#### Aliases

    !songs
    !song

<a name="RequestCommand"></a>
### Request

Requests a song via YouTube, SoundCloud, Twitch, radio streams or by name. If the song was successfully found the song will be added to the queue.

#### Usage

    !request <link or name of song>

#### Aliases

    !play


#### Tag Example

    @AvaIre play <name of song>
    @AvaIre can you find me some chill music?

<a name="ResumeCommand"></a>
### Resume

Resumes the song that was playing before.

The **DJ** role is required to run this command.

#### Usage

    !resume

<a name="ShuffleCommand"></a>
### Shuffle

Shuffles the songs waiting in the queue.

The **DJ** role is required to run this command.

#### Usage

    !shuffle

<a name="SkipCommand"></a>
### Skip

Skips the song that is currently playing.

The **DJ** role is required to run this command.

#### Usage

    !skip

<a name="VolumeCommand"></a>
### Volume

Changes the volume of the music, by default the music will be playing at 50% volume.

The **DJ** role is required to run this command.

#### Usage

    !volume <volume>

<a name="VoteSkipCommand"></a>
### Vote Skip

Votes to skip the song that is currently playing. If 50% or more of the people listening vote to skip, the song will be skipped.

#### Usage

    !voteskip

#### Aliases

    !vskip

<a name="search"></a>
## Search Commands

All commands in the _Search_ module use the `>` prefix.

<a name="GfycatCommand"></a>
### Gfycat

Gets a random gif from [gfycat.com](https://gfycat.com/) with the given tags.

#### Usage

    >gfycat [tag]

#### Aliases

    >gif

<a name="DuckDuckGoCommand"></a>
### Search

Searches DuckDuckGo.com with the given query and returns the first four results.

#### Usage

    >search <query>

#### Aliases

    >ddg
    >g

<a name="UrbanDictionaryCommand"></a>
### Urban Dictionary

Get the definition of a word or sentence from [urbandictionary.com](http://www.urbandictionary.com/).

#### Usage

    >urbandictionary [word or sentence]

#### Aliases

    >urban

<a name="XKCDCommand"></a>
### XKCD

Gets the latest [xkcd](https://xkcd.com/) comic, or the comic with the given ID.

#### Usage

    >xkcd [comic ID]


<a name="system"></a>
## System Commands

All commands in the _System_ module use the `;` prefix.

System commands are limited to **Bot Administrators only**, which means to say the following.

 - Bot Administrators Only commands refer to the commands only a bot admin can use.
 - Bot Administrators Only commands do **not** refer to the owner of the server.
 - Bot Administrators is a person who is **hosting** their own bot, and their **ID** is inside of **config.json**.
 - You are **not** a bot admin if you invited the bot using **discordbots.org** or other invitation links.

<a name="BlacklistAddCommand"></a>
### Blacklist Add

Adds a user to the bot blacklist. This will prevent the user from using any of Ava's features and interacting with the bot in **any** server.

#### Usage

    ;bla <user ID> [reason]

<a name="BlacklistRemoveCommand"></a>
### Blacklist Remove

Removes a user from the bot blacklist, allowing them to interact with the bot again.

#### Usage

    ;blr <user ID>

<a name="BotAdminAddCommand"></a>
### Bot Admin Add

Add a user ID to the bot administrators list temporarily. If the user's ID isn't in config.json when the bot restarts, the user will be removed from the list.

> {tip} This allows the user to run all system commands, this includes the [;bar](#botadminremove) command.

#### Usage

    ;baa <user ID>

<a name="BotAdminListCommand"></a>
### Bot Admin List

Lists all user IDs currently in the bot administrators list.

#### Usage

    ;bal

<a name="BotAdminRemoveCommand"></a>
### Bot Admin Remove

Removes a user ID from the bot administrators list. If the user's ID is in config.json, their ID will be added back to the administrators list when the bot restarts.

#### Usage

    ;bar <user ID>

<a name="BroadcastCommand"></a>
### Broadcast

Prepares a broadcast message and returns a unique ID for the message as well as how it's going to look like. To send the message use the [broadcast send](#broadcastsend) command. Broadcast message IDs are stored for two minutes before being deleted.

#### Usage

    ;broadcast <message>

#### Aliases

    ;bc

<a name="BroadcastSendCommand"></a>
### Broadcast Send

Broadcasts the message linked to the given ID. If the ID is valid the message linked to that ID will be broadcasted to every server the bot is in. The message will be sent to five servers at a time, with 0.5 second delay.

#### Usage

    ;broadcastsend <ID>

#### Aliases

    ;bcsend

<a name="EvalCommand"></a>
### Eval

Evaluates and executes raw JavaScript code.

> {tip} Messing around too much with this command can cause crashes and other funny things to happen since code is being evaluated within the bot while it's running.

#### Usage

    ;eval <code>

<a name="ModuleDisableCommand"></a>
### Module Disable

Disabling a module prevents anyone that isn't a bot administrator from running any commands in that module until the bot is restarted or the module is enabled again. Modules are the command categories, for example [administration](#administration), [fun](#fun), [music](#music) and so forth.

**Note:** The system module cannot be disabled.

> {tip} You don't have to type out the full module/category name, simply typing the first few characters are fine.

#### Usage

    ;md <module>

<a name="ModuleEnableCommand"></a>
### Module Enable

Enables a given module. Modules are the command categories, for example [administration](#administration), [fun](#fun), [music](#music) and so forth.

> {tip} You don't have to type out the full module/category name, simply typing the first few characters are fine.

#### Usage

    ;me <module>

<a name="RebootCommand"></a>
### Reboot

Restarts the bot. If there are any active voice connections all the music will be stopped, the queue will be cleared and a voice maintenance message will be sent instead. Once the message is over the rebooting process will continue.

#### Usage

    ;reboot

#### Aliases

    ;restart

<a name="ReloadCommand"></a>
### Reload

Reloads the given property.

#### Usage

    ;reload lang
    ;reload service
    ;reload database
    ;reload cmd <command>
    ;reload event <event>

#### Aliases

    ;rl

<a name="RuntimeStatisticsCommand"></a>
### Runtime Stats

Returns information about the bot and other runtime statistics.

#### Usage

    ;rstats

#### Aliases

    ;stats

<a name="SafeRebootCommand"></a>
### Safe Reboot

Restarts the bot similar to the [reboot](#reboot) command. However unlike that command, using the safe reboot will wait for all voice connections to drop before restarting.

#### Usage

    ;safereboot

#### Aliases

    ;sreboot

<a name="setstatus"></a>
### Set Status

Sets the status of the bot. If no status is provided, the bot will cycle config-defined status messages.

#### Usage

    ;setstatus [status/Twitch URL]

#### Aliases

    ;status

<a name="SetServerTypeCommand"></a>
### Set Server Type

Sets the server to the given type. This allows selfhosters with little knowledge on SQL to set their server to a particular type. Server types control reward ratios, the amount of alias slots, playlists and so forth.

#### Usage

    ;sst <type> [server ID]

<a name="utility"></a>
## Utility Commands

All commands in the _Utility_ module use the `!` prefix.

<a name="ExpandUrlCommand"></a>
### Expand URL

Unshorten a shortened URL.

#### Usage

    !expand [url]

#### Aliases

    !e

<a name="FeedbackCommand"></a>
### Feedback

Send feedback about Ava back to the developers and the staff team, any message passed to the command will be sent in the [#feedback](https://discord.gg/tAmWcbK) channel on [AvaIre Central](https://discord.gg/gt2FWER).

#### Usage

    !feedback <message>

<a name="LeaderboardCommand"></a>
### Leaderboard

Displays the server's level leaderboard with the user's name, rank, level and XP. The response is paginated to show 10 users per page.

The **[Levels & Experience](#level)** feature must be enabled to run this command.

#### Usage

    !leaderboard [page]

#### Aliases

    !top

<a name="InviteCommand"></a>
### Invite

Displays the OAuth2 invite link for the bot.

#### Usage

    !invite

#### Aliases

    !join

<a name="IPInfoCommand"></a>
### IP Info

Gives information about the given IP address

#### Usage

    !ipinfo <address>

<a name="PingCommand"></a>
### Ping

Ping, Pong.

#### Usage

    !ping

#### Aliases

    !pingme

<a name="RankCommand"></a>
### Rank

Displays the user's rank, level, XP and how much XP they need to level up.

The **[Levels & Experience](#level)** feature must be enabled to run this command.

#### Usage

    !rank

#### Aliases

    !level

<a name="RemindCommand"></a>
### Remind

Sets a message you would like to be reminded of later. The message can be anything while the time format has to follow suit with **XhXXmXXs** to delay the message where X represents a number. You can freely alter the time definition; available time units are hours (`h`), minutes (`m`) and seconds (`s`). Here are some examples.

 - **1h25m52s** = 1 hour, 25 minutes and 52 seconds of delay.
 - **2h16s** = 2 hours and 16 seconds of delay.
 - **30m** = 30 minutes of delay.

#### Usage

    !remind <time> <message>

#### Aliases

    !rem

<a name="ShortenUrlCommand"></a>
### Shorten URL

Shorten a URL using [goo.gl](https://goo.gl/).

#### Usage

    !shorten [url]

#### Aliases

    !s

<a name="SourceCommand"></a>
### Source

Gives you the source code for the bot, or the code for a given command.

#### Usage

    !source [command]

<a name="StatsCommand"></a>
### Stats

Displays information about Ava and some related stats. The following information will be returned.

 - Bot ID
 - Author of the bot
 - The current version of the bot
 - The last few changes to the latest version of Ava
 - Library the bot is written in
 - How many database queries have been run
 - How many messages have been received
 - How many servers Ava is playing music in right now
 - How many servers Ava is in
 - How many commands have been run
 - How much memory Ava is using
 - How many users Ava knows about (total, total online, unique and unique online)
 - How many channels Ava knows about (total, text and voice)
 - How long Ava has been online

#### Usage

    !stats

#### Aliases

    !about

<a name="UptimeCommand"></a>
### Uptime

Displays how long the bot has been online.

#### Usage

    !uptime

<a name="VersionCommand"></a>
### Version

Displays the current version of Ava you're running. If the version is oudated the new version will be shown as well as what type of changes have been made.

#### Usage

    !version

<a name="CreateYesNoPollCommand"></a>
### Yes/No Poll

Creates a poll with a message. Users can then vote yes or no on the poll; when the given amount of time the poll will automatically close and show the result of the poll. The time format is the same as the one used with [remind](#remind).

#### Usage

    !yesnopoll <time> <message>

#### Aliases

    !ynpoll
    !poll
