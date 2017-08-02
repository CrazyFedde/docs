# Command List

Below you'll find a list of all **84** commands that Ava has, along with a short description of what each command does. If you'd like to know more about the command, like what permissions or roles are required to run the command, different aliases or anything similar you can click on the command links and you'll be taken to a more descriptive version of the command.

## Table of Contents

- [Help Command](#help)
- [Administration](#administration)
- [Fun](#fun)
- [Music](#music)
- [Search](#search)
- [System](#system)
- [Utility](#utility)

<a name="help"></a>
## Help Command

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [.help](/docs/{{version}}/commands#HelpCommand)  | Lists all the command modules  |
| [.help [module]](/docs/{{version}}/commands#HelpCommand)  | Lists all the commands in the given module  |
| [.help [command]](/docs/{{version}}/commands#HelpCommand)  | Displays information about the provided command  |

<a name="administration"></a>
## Administration

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [.ai](/docs/{{version}}/commands#AiCommand)  | Toggles the AI on or off for the current channel  |
| [.alias [alias] [command]](/docs/{{version}}/commands#AliasCommand)  | Binds or unbinds custom command aliases  |
| [.aliases [page]](/docs/{{version}}/commands#AliasesCommand)  | Lists all command aliases for the server  |
| [.ban <user\> [reason]](/docs/{{version}}/commands#BanCommand)  | Bans the tagged user with the given reason  |
| [.changeprefix <module\> [prefix]](/docs/{{version}}/commands#ChangePrefixCommand)  | Changes the prefix Ava uses  |
| [.channel](/docs/{{version}}/commands#ChannelCommand)  | Displays the status of modules for the current channel  |
| [.goodbye](/docs/{{version}}/commands#GoodbyeCommand)  | Toggles the goodbye module on or off for the current channel  |
| [.goodbyemessage [message]](/docs/{{version}}/commands#GoodbyeMessageCommand)  | Sets the goodbye message for the current channel  |
| [.kick <user\> [reason]](/docs/{{version}}/commands#KickCommand)  | Kicks the tagged user from the server  |
| [.language [local]](/docs/{{version}}/commands#LanguageCommand)  | Changes or lists the languages Ava supports  |
| [.level](/docs/{{version}}/commands#LevelCommand)  | Toggles the level system on or off for the current server  |
| [.levelalerts [channel]](/docs/{{version}}/commands#LevelAlertsCommand)  | Toggles the level alerts system on or off for the current server  |
| [.modlog](/docs/{{version}}/commands#ModlogCommand)  | Toggles modlog on or off for the current channel  |
| [.modules](/docs/{{version}}/commands#CommandModulesCommand)  | Shows the status of the given command modules for the current channel, and globally  |
| [.purge <amount\> [user]](/docs/{{version}}/commands#PurgeCommand)  | Purge old messages from the current channel  |
| [.serverid](/docs/{{version}}/commands#ServerIdCommand)  | Shows the server ID |
| [.serverinfo](/docs/{{version}}/commands#ServerInfoCommand)  | Shows information about the server  |
| [.setup [feature]](/docs/{{version}}/commands#SetupCommand)  | Helps you setup features within Ava for the server  |
| [.slowmode [limit] [decay]](/docs/{{version}}/commands#SlowmodeCommand)  | Toggles slowmode on or off for the current channel  |
| [.softban <user\> [reason]](/docs/{{version}}/commands#SoftbanCommand)  | Bans the tagged user with the given reason  |
| [.togglemodule <module\> [channel\|all]](/docs/{{version}}/commands#ToggleModuleCommand)  | Toggles the given module on or off for the current channel or the whole server  |
| [.userid [user]](/docs/{{version}}/commands#UserIdCommand)  | Shows the ID of the tagged user  |
| [.userinfo [user]](/docs/{{version}}/commands#UserInfoCommand)  | Shows information about the tagged user  |
| [.welcome](/docs/{{version}}/commands#WelcomeCommand)  | Toggles the welcome module on or off for the current channel  |
| [.welcomemessage](/docs/{{version}}/commands#WelcomeMessageCommand)  | Sets the welcome message for the current channel  |

<a name="fun"></a>
## Fun

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [>blah](/docs/{{version}}/commands#BlahCommand)  | Blah?  |
| [>canyounot](/docs/{{version}}/commands#CanYouNotCommand)  | Can you not...?  |
| [>chucknorris](/docs/{{version}}/commands#ChuckNorrisCommand)  | Gets a random 100% true fact about Chuck Norris  |
| [>coin](/docs/{{version}}/commands#CoinCommand)  | Flips a coin for heads or tails  |
| [>dice [dice format]](/docs/{{version}}/commands#DiceCommand)  | Rolls a set of dice  |
| [>holiday](/docs/{{version}}/commands#HolidayCommand)  | Find out of today is a holyday  |
| [>lenny](/docs/{{version}}/commands#LennyCommand)  | ( ͡° ͜ʖ ͡°)  |
| [>meme <meme\> [top text] [bottom text]](/docs/{{version}}/commands#MemeCommand)  | Creates a custom meme of the given type  |
| [>randomcat](/docs/{{version}}/commands#RandomCatCommand)  | Gets a random cat image from the internet  |
| [>randomdog](/docs/{{version}}/commands#RandomDogCommand)  | Gets a random dog image from the internet  |
| [>repeat [message]](/docs/{{version}}/commands#RepeatCommand)  | Makes Ava repeat whatever you say  |
| [>rip](/docs/{{version}}/commands#RipCommand)  | Pay your respects  |
| [>roll [min] [max]](/docs/{{version}}/commands#RollCommand)  | Rolls a random number between 1 and 100, or between the numbers given  |
| [>say [message]](/docs/{{version}}/commands#SayCommand)  | Makes Ava say whatever you want  |
| [>shrug](/docs/{{version}}/commands#ShrugCommand)  | ¯\\_(ツ)_/¯  |
| [>slowclap](/docs/{{version}}/commands#SlowClapCommand)  | Clap... Clap... Clap...  |

<a name="music"></a>
## Music

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [!flushqueue](/docs/{{version}}/commands#FlushQueueCommand)  | Flushes the music queue, removing all songs currently waiting in the queue  |
| [!movehere](/docs/{{version}}/commands#MoveHereCommand)  | Moves the bot into the same voice channel you're in  |
| [!pause](/docs/{{version}}/commands#PauseCommand)  | Pauses the song that is currently playing  |
| [!playlist](/docs/{{version}}/commands#PlaylistCommand)  | Main command used to manage the custom music playlists  |
| [!queue](/docs/{{version}}/commands#QueueCommand)  | Lists all the songs in the music queue  |
| [!repeatsongs](/docs/{{version}}/commands#RepeatMusicQueueCommand)  | Repeats the songs currently in the music queue  |
| [!request [name/url]](/docs/{{version}}/commands#RequestCommand)  | Request a song via YouTube, SoundCloud, Twitch, radio streams or by name  |
| [!resume](/docs/{{version}}/commands#ResumeCommand)  | Resumes the song that was playing before  |
| [!shuffle](/docs/{{version}}/commands#ShuffleCommand)  | Shuffles the songs waiting in the queue  |
| [!skip](/docs/{{version}}/commands#SkipCommand)  | Skips the song that is currently playing  |
| [!volume <vol\>](/docs/{{version}}/commands#VolumeCommand)  | Changes the volume of the music  |
| [!voteskip](/docs/{{version}}/commands#VoteSkipCommand)  | Votes to skip the song that is currently playing  |

<a name="search"></a>
## Search

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [>gfycat [tags]](/docs/{{version}}/commands#GfycatCommand)  | Gets a random gif from [gfycat.com](https://gfycat.com/)  |
| [>search <query\>](/docs/{{version}}/commands#DuckDuckGoCommand)  | Searches DuckDuckGo.com with your given query  |
| [>urban [word]](/docs/{{version}}/commands#UrbanDictionaryCommand)  | Get the definition of a word or sentence from [urbandictionary.com](http://www.urbandictionary.com/)  |
| [>xkcd [number]](/docs/{{version}}/commands#XKCDCommand)  | Gets the latest [xkcd](https://xkcd.com/) comic, or the comic with the given id.  |

<a name="system"></a>
## System

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [;bla <user\> [reason]](/docs/{{version}}/commands#BlacklistAddCommand)  | Add a user to the bot blacklist  |
| [;blr <user\>](/docs/{{version}}/commands#BlacklistRemoveCommand)  | Removes a user from the bot blacklist  |
| [;baa <user\>](/docs/{{version}}/commands#BotAdminAddCommand)  | Add a user ID to the bot administrators list temporarily  |
| [;bal](/docs/{{version}}/commands#BotAdminListCommand)  | Lists all the user IDs that are currently in the bot administrators list  |
| [;bar <user\>](/docs/{{version}}/commands#BotAdminRemoveCommand)  | Removes a user ID from the bot administrators list  |
| [;broadcast <message\>](/docs/{{version}}/commands#BroadcastCommand)  | Prepares a broadcast message  |
| [;broadcastsend <id\>](/docs/{{version}}/commands#BroadcastSendCommand)  | Broadcasts the message linked to the given ID  |
| [;eval <code\>](/docs/{{version}}/commands#EvalCommand)  | Evaluates and executes raw JavaScript code  |
| [;md <module\>](/docs/{{version}}/commands#ModuleDisableCommand)  | Disable the given command module for all servers  |
| [;me <module\>](/docs/{{version}}/commands#ModuleEnableCommand)  | Enable the given command module for all servers  |
| [;reboot](/docs/{{version}}/commands#RebootCommand)  | Restarts the bot instance  |
| [;reload <property\>](/docs/{{version}}/commands#ReloadCommand)  | Reloads the given property  |
| [;rstats](/docs/{{version}}/commands#RuntimeStatisticsCommand)  | Displays information about the bot, and other runtime statistics  |
| [;safereboot](/docs/{{version}}/commands#SafeRebootCommand)  | Restarts the bot instance safely |
| [;sst](/docs/{{version}}/commands#SetServerTypeCommand)  | Sets the type of the current server or by ID |

<a name="utility"></a>
## Utility

| Command           | Short Description      |
| ----------------- |:---------------------- |
| [!expand <url\>](/docs/{{version}}/commands#ExpandUrlCommand)  | Unshorten an URL  |
| [!feedback <message\>](/docs/{{version}}/commands#FeedbackCommand)  | Gives feedback about the bot  |
| [!leaderboard](/docs/{{version}}/commands#LeaderboardCommand)  | Sends the level leaderboard for the current server  |
| [!invite](/docs/{{version}}/commands#InviteCommand)  | Sends the link to invite Ava to your server  |
| [!ping](/docs/{{version}}/commands#PingCommand)  | Ping, Pong  |
| [!rank](/docs/{{version}}/commands#RankCommand)  | Displays the users rank, level and XP if Leveling is enabled  |
| [!remind <time\> <message\>](/docs/{{version}}/commands#RemindCommand)  | Sets a message you would like to be reminded of later  |
| [!shorten <url\>](/docs/{{version}}/commands#ShortenUrlCommand)  | Shorten a URL using [goo.gl](https://goo.gl/)  |
| [!source [command]](/docs/{{version}}/commands#SourceCommand)  | Sends a link to the source code for the given command  |
| [!stats](/docs/{{version}}/commands#StatsCommand)  | Displays information and stats about Ava  |
| [!uptime](/docs/{{version}}/commands#UptimeCommand)  | Displays how long Ava has been online for  |
| [!version](/docs/{{version}}/commands#VersionCommand)  | Displays the current version of Ava  |
| [!yesnopoll <time\> <poll\>](/docs/{{version}}/commands#CreateYesNoPollCommand)  | Creates a poll people can vote on  |
