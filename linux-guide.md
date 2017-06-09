# Linux Guide

- [Prerequisites](#prerequisites)
    - [Linux Server](#server)
    - [Software](#software)
- [Installing Requirements](#install-requirements)
    - [NodeJS & NPM](#install-node)
    - [Git - Source Control](#install-git)
- [Installing Ava](#install-ava)
- [Configuration of Ava](#configuration)
- [Running the bot](#running-the-bot)

<a name="prerequisites"></a>
## Prerequisites

> {tip} This guide assumes you already have a basic understanding of Linux based systems and programs like **vim** for editing files in the command line, since the whole guide will be taking place in the command line.

<a name="server"></a>
#### Linux Server

 * __Type:__ A small stable VPS, a dedicated machine is a bit overkill unless you're already using it for other things as well.
 * __OS:__ Ubuntu LTS or latest, optionally Debian 8
 * __Ram:__ May work on 256 MB, 512MB is recommended. If you plan on having it on just a few servers. Scale up if necessary.
 * __Processor:__ Single core @ 2.60 GHz or higher will work just fine, as above.
 * SSH access to the server.

<a name="software"></a>
#### Software

 * SSH client, i.e. [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) connecting and executing commands on the server

<a name="install-requirements"></a>
## Installing Requirements

Start by logging into your server via your SSH client.

<a name="install-node"></a>
### Installing NodeJS & NPM

We'll be using NodeJS to run Ava, if you don't already have NodeJS and NPM installed, you can install it with the following commands.

    sudo apt install nodejs

If your server doesn't have the NodeJS reposetories saved you can try using updating the repositories and re-atempting to install NodeJS like the command below.

    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    sudo apt install -y nodejs

<a name="install-git"></a>
### Installing Git

Next we'll install Git to be able to download and update Ava, git will also be used later on if you want to update Ava to the latest version.

Start off by checking if git is already installed, some services that offers Linux servers comes with Git pre-installed, you can check if git is installed by running:

    git --version 

If the command is not found you can install git by running

    sudo apt install git

<a name="install-ava"></a>
## Installing Ava

Next, we'll retrieve the AvaIre GitHub repository, we will be using Git to install Ava so it will be easier to update later on.

You'd want to figure out where you want the bot to be downloaded. When you've found the location of your choice, clone the Ava repository into the folder by using the following command.

    git clone https://github.com/AvaIre/AvaIre.git .

You have now successfully cloned the AvaIre Git repository, next we'll need to install all the dependencies, for this we'll be using Yarn, to install that just run:

    npm install -g yarn

Now that we have yarn installed we can run use yarn to install all of Avas dependencies with the correct version number for everything so you're sure everything matches up, just run:

    yarn

This will install everything Ava needs to run, if you're running the command for the first time it might take a minute or two to install everything, just get a cup of coffee while Yarn does its thing.

<a name="configuration"></a>
## Configuration of Ava

Next we'll need to configure Ava so the bot can connect and communicate with users, in the folder Ava was installed in you should find a file called `confg.example.json`, rename that file to `config.json`.

    cp confg.example.json config.json

You can now open the new `config.json` file in vim, next we'll need to setup a database the Ava can use, Ava requires a database to store things like custom playlists, aliases, channel and server data, and a lot of other things, if you don't have any experiance with `MySQL` databases you can also use `SQLite` which is a lot easier to setup, by default Ava comes with a MySQL database config setup.

If you're planning on using a `MySQL` database you can leave the database parts of the config as is, if you wanna change to a `SQLite` database setup you can find an example of a [SQLite config setup here](https://gist.github.com/Senither/0f270f8b3579b96c0661c990b3d87fbf), if you're using `SQLite` config example just leave the database parts of the config as is and you should be fine.

Now that the database is in order you'll need to put your Discord Bot Application token in the `bot.token` property, you can find your bot token under your Discord Application dashboard, if you don't have a Discord bot application setup you can create one easily by following these steps.

 1. Start by heading to [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me), once you're there you can create a new application, you can name it whatever you want and give it a fancy picture and description if you want to, once you're done click **Create App**.
 2. Your application should now have been created, next click on the **Create a Bot User** button, this will convert the application to a bot user application.
 3. Now that you have a user bot application you can get your bot token under the **App Bot User** section.

> {tip} If you want other people to be able to invite the bot you must check the **Public Bot** options under your **App Bot User** application settings, if you don't do that you will be the only one that can invite the bot to servers.

On your bot application dashboard you'll also be able to find your bot client id, we'll need that later to invite the bot so keep onto it.

If you want a more in-detail guide and walkover for the [configuration](/docs/{{version}}/configuration) file you can checkout the [Configuration](/docs/{{version}}/configuration) page, all the settings and options are covered in more detail on that page with guides on how to setup each option.

<a name="running-the-bot"></a>
## Running the bot

Congratulations, your AvaIre instance should now be ready to launch!

To start the bot head into the `/scripts` folder, there you'll find a start and update scripts for linux systems, just run the `linux-start.sh` file and you should be good to go.

If the bot runs without any errors, you have had success so far!

> {tip} It is recommend that you run the bot in a screen to prevent the bot from disconnecting when you disconnect from the server.

Now you'll need to invite your bot to your server so you can actually use it, take your bots client id from ealier and pop it into a URL like this without the less than and greater than symbols.

    https://discordapp.com/oauth2/authorize?&client_id=<client id>&scope=bot

Just replace the `<client id>` with your actually bot application id, if you don't have your client id you can find it on the [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me) page, just click on your application, the client ID is at the very top under the **App Details** section.

Go to the URL in a web browser, select your server and ht `Authorize`, your bot should now be on your server.

You can test simple functionality by running the ping command in a text channel that the bot can see. If it answers "Pong!", then congratulations, you have successfully set up AvaIre!

And that's it! You are now ready to start using your very own AvaIre instance!
Keep in mind, if you have further questions or need help, we're around over at our official server, [AvaIre Central](https://discord.gg/gt2FWER)!

On the behalf of the AvaIre team, we hope you enjoy your bot!
