# Configuration

 - [Overview](#overview)
 - [Properties](#properties)
     - [Environment](#environment)
     - [Bot Tokens](#tokens)
     - [Database](#database)
     - [Playing](#playing)
     - [Bot Access](#botaccess)
     - [API Keys](#apis)

<a name="overview"></a>
## Overview

This is an overview of the `config.json` files content, when you're self-hosting AvaIre make sure you can find the `config.json` file in the root of the project, if you can't find the file copy the `config.json.example` file and rename it to `config.json` and you should be good to go.

<a name="properties"></a>
## Properties

Configuration properties.

<a name="environment"></a>
### Envioronment

The environment property should always return a single string that represents the current application environment, if the environment is not valid the fallback(development mode) will be used instead. The following enviornments work within Ava.

 - Production 
    - Limits error logging to the console as much as possible, and eables all features. Error logging is stile done to-file which will be stored in `storage/logs/*`.
 - Testing
    - Used during tests, this environment will be dynamicly be set when tests are run, anything that might hit a database will use a in-memory SQLite database instead while this envioronment is set.
 - Development
    - Logs anything and everything to the console, some features like stats updates for the bot will also be disabled to prevent Avas development version stats to be listed publicly.

<a name="tokens"></a>
### Bot Tokens

The bot tokens, or `bot` field is a small object with two fields, *token* and *oauth*.

#### Token

The bot token is the bot application token, if you don't already have a bot token you can create by following these steps.

 1. Start by heading to [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me), once you're there you can create a new application, you can name it whatever you want and give it a fancy picture and description if you want to, once you're done click **Create App**.
 2. Your application should now have been created, next click on the **Create a Bot User** button, this will convert the application to a bot user application.
 3. Now that you have a user bot application you can get your bot token under the **App Bot User** section.

> {tip} If you want other people to be able to invite the bot you must check the **Public Bot** options under your **App Bot User** application settings, if you don't do that you will be the only one that can invite the bot to servers.

#### OAuth

The oauth field should contain a valid invite link for the bot, the invite link should look like this:

    https://discordapp.com/oauth2/authorize?&client_id=<your client id>&scope=bot&permissions=66186303

Just replace the `<your client id>` with your actually bot application id, you can find your bot application id on the [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me) page, just click on your application, the client ID is at the very top under the **App Details** section.

> **Note**: The client id is **not** your client secret, but your public application client id.

<a name="database"></a>
### Database

The database properties determines what type of database Ava and connection information that should used, out of the bot Ava supports three database types.

 - MySQL
    - This should be used for any large bots where shards is required, using MySQL can also be a lot easier in many cases to setup since Ava comes with a MySQL setup out of the box.
 - SQLite3 - Flatfile Database
    - This store the entire database in a single file in the root directory of the application, this option is fast but may somtime not work when there is a lot of database activity at the same time.
 - SQLite3 - In Memory Database
    - This stores the database in-memory, this means that when the bot restarts the entire database will be deleted in the process, this should only be used for tests.

> {tip} Everytime you start AvaIre the database manager will check if all the migrations has been rolled out, if there is one missing the corresponding tables and columns will be created/updated.

#### MySQL Setup

```json
"database": {
    "type": "mysql",
    "database": "avaire",
    "host": "localhost",
    "user": "username",
    "password": "password"
}
```

The host should be the host the MySQL database is hosted on, you can add your port to the host by suffixing it with a colon(:) followed by the port you use, for example `localhost:3307`, if the port is left out the port will use the default `3306` port. If you're running the bot localy and have something like [XAMPP](https://www.apachefriends.org/index.html) or [WampServer](http://www.wampserver.com/en/) installed then you should be fine leaving the host as is.

#### SQLite3 Setup

```json
"database": {
    "type": "sqlite3",
    "filename": "./database.sqlite"
}
```

Make sure to create a bank text file in the root of the application called `database.sqlite` for SQLite to work properly, if you want to use an in-memory database(Which seems kinda silly unless you're testing the database) you can use the following setup.

```json
"database": {
    "type": "sqlite3",
    "filename": ":memory:"
}
```

<a name="playing"></a>
### Playing

The playing property is a simple JSON string array, anything you put into the array will be randomly selected by Ava and a certain interval the selected item will be set as the bots playing status, out of the bot the array will only have one property, but any number of strings could be added to the array.

<a name="botaccess"></a>
### Bot Access

The bot access property is a simple JSON string array containing the IDs of users who should have full access to the system commands in the bot, you can find peoples user IDs by using the [User ID](/docs/{{version}}/commands#user-id) or [User Info](/docs/{{version}}/commands#user-info) commands. You can add people to this admin list temporarily by using the system [Bot Admin Add](/docs/{{version}}/commands#botadminadd) command.

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

#### API.AI

[API.AI](https://api.ai/) is a really cool service that provides you with "AI agents" that can process text and voice and allows you to setup your own rules for different input, Ava uses a custom public agent that allows users to ask Discord related questions and data being used live, you can find all the AI intent handlers in [github.com/AvaIre/AvaIre/tree/master/app/services/ai/intents](https://github.com/AvaIre/AvaIre/tree/master/app/services/ai/intents), if you're using the smalltalk agent from [api.ai](https://api.ai/) the response will skip the intend handles and just be sent back directly to the user. If you don't already have a [api.ai](https://api.ai/) token you can create a simple AI agent in minutes by following these steps.

 1. Head over to [api.ai](https://api.ai/) and signup using your email or google account, once you're logged in you can create a new AI agent.
 2. When creating the new agent you can either make a public or private agent, if the agient is public other people will be able to use your agent for their own projects.
 3. Setup a AI agent name and description, you can also start adding some sample data and select that language you want the bot to use, once you're done click the **Save** button in the top right.
 4. Now that your agent is created you can start making some custom intents or enabled prebuilt agents.
 5. Once you're done adding intents you can head over to your agents settings in the top left, there you'll find your **Client access token**, you can copy that into the `config.json` file, the AI feature for Ava will now use your custom agent!

#### Discord Stats

The Discord stats field refers to the [https://bots.discord.pw/api](https://bots.discord.pw/api) API, if the bot has been added to the site, the API can be used to update the server count for the bot, however due to requirements and regulations for adding a bot to [https://bots.discord.pw/](https://bots.discord.pw/), using a carbon copy of Ava won't get the bot accepted, so if you're using a custom version of Ava you'll have to put in quite a few man-hours adding features that doesn't already exists within the project to use this API.

If you're adding custom features to the project and you think other people might be interested in using the features you've made, feel free to send a [pull request on github](https://github.com/Senither/AvaIre) or come talk to the developers for the project in our [Discord server](/support).