# Configuration

 - [Overview](#overview)
 - [Properties](#properties)
     - [Environment](#environment)
     - [Discord Application](#discord-app)
     - [Database Settings](#database)
     - [Bot Status (Playing)](#status)
     - [Music Activity Settings](#music-activity)
     - [Bot Access (Bot Admins)](#botaccess)
     - [Webhook Server Log](#webhook)
     - [Sentry.io Error Logging](#sentry)
     - [Prometheus Metrics & Spark API](#metrics)
     - [API Keys](#apis)

<a name="overview"></a>
## Overview

This is an overview of the `config.yml` files content, when you're self-hosting AvaIre make sure you can find the `config.yml` file in the root of the project, if you can't find the file you'll need to run the binary jar file 
 
    java -jar AvaIre.jar

You can also find a lot of information in the `config.yml` file, for an example of what a default `config.yml` file should look like, check the default file on github at [github.com/avaire/avaire/blob/master/src/main/resources/config.yml](https://github.com/avaire/avaire/blob/master/src/main/resources/config.yml)

<a name="properties"></a>
## Properties

Configuration properties.

<a name="environment"></a>
### Environment

The application environment determines what is logged to the console, and what applications are loaded, this is to give a better user experience since having the console flooded with information can be very overwhelming if you don't know what you're looking at.

AvaIre supports two different environments, "production" and "development"

Production is used for minimal console output and for all parts of the application to be enabled. Development is used for debugging messages and preventing some parts of the application from running, to stop in-development changes from ruining the production environment. 

<a name="discord-app"></a>
### Discord Application

Discord application information is things like your application token, application id, application secret, etc. To run a Discord bot you'll need an application token, if you don't already have an application with discord you can easily create one in two minutes.

 1. Start by heading to [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me), once you're there you can create a new application, you can name it whatever you want and give it a fancy picture and description if you want to, once you're done click **Create App**.
 2. Your application should now have been created, next click on the **Create a Bot User** button, this will convert the application to a bot user application.
 3. Now that you have a user bot application you can get your bot token under the **App Bot User** section.

AvaIre needs your Discord application token to login and interact with users, and optionally the application ID for generating invite links people can use to invite the bot to their servers with.

#### Token

This is your Discord application token, if you don't have a Discord application, check the link above and follow the short guide to create one, once you have it, replace the text between the quotes with your token.
The bot token is the bot application token, if you don't already have a bot token you can create by following these steps.

> {tip} If you want other people to be able to invite the bot you must check the **Public Bot** options under your **App Bot User** application settings, if you don't do that you will be the only one that can invite the bot to servers.

#### OAuth

The oauth field should contain a valid invite link for the bot, the invite link should look like this:

    https://discordapp.com/oauth2/authorize?&client_id=<client id>&scope=bot

Just replace the `<client id>` with your actual bot application id, you can find your bot application id on the [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me) page, just click on your application, the client ID is at the very top under the **App Details** section.

> **Note**: The client id is **not** your client secret, but your public application client id.

<a name="database"></a>
### Database

AvaIre uses a database for storing things like custom prefixes, playlists, user XP and levels, statistics, autoroles, aliases and everything else.

AvaIre currently only support the MySQL database type, with support for more types in the works, to get start simply just populate the fields below with your database login information.

> Make sure the database user has permission to create, delete and edit tables in the database you want to use, Ava uses a migration system that will create all the needed tables, and roll out changes between versions automatically, this require creating new tables, and editing and deleting existing tables.

#### MySQL Setup

```yaml
database:
  type: 'mysql'
  database: 'avaire'
  hostname: 'localhost'
  username: 'username'
  password: 'password'
```

The host should be the host the MySQL database is hosted on, you can add your port to the host by suffixing it with a colon(:) followed by the port you use, for example `localhost:3307`, if the port is left out the port will use the default `3306` port. If you're running the bot locally and have something like [XAMPP](https://www.apachefriends.org/index.html) or [WampServer](http://www.wampserver.com/en/) installed then you should be fine leaving the host as is.

#### SQLite3 Setup

Coming soon...

<a name="music-activity"></a>
### Music Activity Settings

Music Activity is a tracking system built into Ava that disconnects the bot from voice channels if no one is listening to music anyway, this can help free up memory and bandwidth that wasn't being used to serve users anyway.

The music activity tracks a few things:

1. When no one is listening to the music, like when the bot is muted, everyone is deafened, or no one is in the voice channel with the bot.
2. If the queue is empty, when you request a song by name the queue will be empty until the user selects the song they want to be played, this applies here, if the last song in the queue is playing it will disconnect once the song is done anyway.
3. If the music is paused, this should be self-explanatory, if you pause the music the bot it will disconnect after awhile unless it is unpaused(resumed).

<a name="status"></a>
### Bot Status (Playing)

Once every minute, Ava will change her "playing" status to something on the playing list, you can define what type of status it is by prefixing the status with one of the options below.

 - watching:something
   - This produces "Watching something"
 - listening:some cool music
   - This produces "Listening to some cool music"
 - streaming:video games
   - This produces "Streaming video games"

If no prefix is given the playing status type will be used instead.

<a name="botaccess"></a>
### Bot Access (Bot Administrators)

The bot access property is a string array containing the IDs of users who should have full access to the system commands in the bot, you can find peoples user IDs by using the [User ID](/docs/{{version}}/commands#UserIdCommand) or [User Info](/docs/{{version}}/commands#UserInfoCommand) commands.

> Users who are bot administrators will still need the regular Discord permissions to run all the other commands outside of the System category, so bot admins can't use commands like the [ban command](docs/{{version}}/commands#BanCommand) without the right Discord permissions.

<a name="webhook"></a>
### Webhook Server Log

The webhook option is only used for logging information about servers when the bot joins or leaves a server, this can give a nice overview of what servers the bot is joining or when it leaves a server, which server it was.

<a name="sentry"></a>
### Sentry.io Error Logging

Sentry.io is an open source error tracking service, it can provide a lot of helpful information to developers on what is going wrong, and where in real-time, Sentry.io uses a DSN url for establishing a link between the bot and their service, the DSN url is used in Ava to log warnings, errors, and exceptions.

To learn more, checkout: https://sentry.io/welcome/

<a name="metrics"></a>
### Prometheus Metrics & Spark API

Ava uses Prometheus metrics for tracking a long list of different things within the application during runtime, the metrics are then displayed using Grafana to users on a web-dashboard using graphs.

Along with the metrics, a stats and guilds API is also enabled, displaying stats per-shard, and globally with guild, channel, and user data, as well as the shard ID and the shard status, while the guild API allows getting information about one or more guilds at a time, as well as checking if the bot is on the given server ID or not, this is used by the AvaIre dashboard.

The metrics stats are exposed on `ip:port/metrics`, the stats API are exposed on `ip:port/stats`, and the guilds API are exposed on `ip:port/guilds/<guild ids>` and `ip:port:guilds/<guild ids>/exists`

For an real-world example of what the metrics looks like when they're setup using Grafana, checkout: https://status.avairebot.com

For setup guides, see:

 - https://prometheus.io/
 - https://grafana.com/

<a name="apis"></a>
### API Keys

The API Keys properties holds a list of API keys for different services, if the service has a valid API key additional features will be enabled for the bot for the given service.

> **Note:** Any API keys you might use is sensitive and could do a lot of harm if revealed to the public, it is imperative that you don't share these keys with anyone. AvaIre maintainers and staff will **NEVER** ask for your login details or API keys.

#### Google

Googles public API offers a lot of really cool features, within Ava the YouTube API is used to retrieve data for music playback and streaming from YouTube, if you don't already have a google API token you can follow these steps.

 1. Go to [https://console.developers.google.com/](https://console.developers.google.com/) and create a new project by clicking the dropdown menu in the top-left, you can name it whatever you fancy. Nothing else needs to be changed unless you want to change the project ID or the app engine location. Creating the new application might take a little while so get a cub of coffee while google does their thing.
 2. When the creation process is completed, you'll get taken to the Dashboard screen of the project. In the sidebar on the left, click **Library** and click on the **YouTube Data API** option.
 3. When the API page opens, click the **Enable** button in the top bar, this will enable the **YouTube Data API** for your project.
 4. Now that the **YouTube Data API** is enabled we'll have to setup some *credentials* for the application, click on the **Create credentials** button in the top right of the page, you'll be geeted with a few options, for the `Where will you be calling the API from?` field you can select the **Web browser (Javascript)** option, make sure you check **Public data** for the `What data will you be accessing?` option, once you've done that you can create your credentials.
 5. You should now have your API key, you can copy that into the `config.json` file and use all of YouTubes features.

#### DialogFlow

[DialogFlow](https://dialogflow.com/) is a really cool service that provides you with "AI Agents" that can process text and voice and allows you to setup your own rules for different input, Ava uses a custom agent that allows users to ask Discord related questions and data being used live. If you don't already have a [DialogFlow](https://dialogflow.com/) token you can create a simple AI agent in minutes by following these steps.

 1. Head over to [DialogFlow](https://dialogflow.com/) and signup using your email or google account, once you're logged in you can create a new AI agent.
 2. When creating the new agent you can either make a public or private agent, if the agent is public other people will be able to use your agent for their own projects.
 3. Setup an AI agent name and description, you can also start adding some sample data and select the language you want the bot to use, once you're done click the **Save** button in the top right.
 4. Now that your agent is created you can start making some custom intents or enabled prebuilt agents.
 5. Once you're done adding intents you can head over to your agents settings in the top left, there you'll find your **Client access token**, you can copy that into the `config.yml` file, the AI feature for Ava will now use your custom agent!
 
If you want to use the same AI agent Ava uses you can find it on github at: https://github.com/avaire/agent
