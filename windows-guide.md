# Windows Guide

- [Prerequisites](#prerequisites)
    - [Windows System](#windows)
    - [Software](#software)
- [Installing Requirements](#install-requirements)
    - [NodeJS & NPM](#install-node)
    - [Git - Source Control](#install-git)
- [Installing Ava](#install-ava)
- [Configuration of Ava](#configuration)
- [Running the bot](#running-the-bot)

<a name="prerequisites"></a>
## Prerequisites

<a name="windows"></a>
#### Windows

 * 1GB of ram or more
 * Windows 7 and higher
 * Administrator access to the computer

<a name="software"></a>
#### Software

 * [NodeJS & NPM](#install-node)
 * [Git](#install-git)
 * A code editor, i.e. [Notepad++](https://notepad-plus-plus.org/) or [Atom](https://atom.io/) or [Sublime Text](https://www.sublimetext.com/)

<a name="install-requirements"></a>
## Installing Requirements

**General note:** Quite a few steps in this guide will be using administrative permissions. Therefore we recommend that you are logged into an administrator account to not have to type the admin password every time you perform something.

<a name="install-node"></a>
### Installing NodeJS & NPM

We'll be using NodeJS to run Ava, if you don't already have NodeJS and NPM installed, head over to the [NodeJS download page](https://nodejs.org/en/download/) and download the version relevant to your OS bit version. It's pretty straight forward, just make sure that the features tab looks like this.

<img src="/assets/img/guides/nodejs-setup.png" alt="NodeJS Setup">

<a name="install-git"></a>
### Installing Git

Next we'll install Git to be able to download and update Ava, git will also be used later on if you want to update Ava to the latest version.

Start off by going to the [Git download page](https://git-scm.com/downloads) and download the Windows installer.

 > {tip} **Note:** The installation process of Git has to go exactly as described below, otherwise you will have to take longer ways around!

Once downloaded, run the installer. Read the license and continue. Once you get to the component selection, **make sure that it looks at least like this!**

<img src="/assets/img/guides/git-setup-1.png" alt="Git Setup">

After selecting the start menu folder, this is where things get precise. **Make sure that you tick the boxes exactly as follows!**

<img src="/assets/img/guides/git-setup-2.png" alt="Git Setup">
<img src="/assets/img/guides/git-setup-3.png" alt="Git Setup">
<img src="/assets/img/guides/git-setup-4.png" alt="Git Setup">
<img src="/assets/img/guides/git-setup-5.png" alt="Git Setup">
<img src="/assets/img/guides/git-setup-6.png" alt="Git Setup">

From here on just continue with the installation process until Git is installed.

<a name="install-ava"></a>
## Installing Ava

Next, we'll retrieve the AvaIre GitHub repository, we will be using Git to install Ava so it will be easier to update later on.

You'd want to figure out where you want the bot to be downloaded. Something simple where you can find it is good, AKA not in the system internals (Possibly some other drive, though NOT A FLASH DRIVE) or optionally your Desktop could be fine.

When you've found the location of your choice, hit `Shift+Right click` and select **Git Bash here**. This will open the Git Bash console. Type the following command into Git Bash:

    git clone https://github.com/AvaIre/AvaIre.git .

Let it clone the Git repository. When it's done, you should have the following output.

<img src="/assets/img/guides/ava-setup.png" alt="Git Setup">

You have now successfully cloned the AvaIre Git repository, next we'll need to install all the dependencies, this is where NPM comes in, while the Console Window is still open run:

    npm install

This will install everything Ava needs to run, if you're running the command for the first time it might take a minute or two to install everything, just get a cup of coffee while NPM does its thing.

<a name="configuration"></a>
## Configuration of Ava

Once Ava has been cloned down into a folder and all the dependencies has been installed we'll need to configure Ava so the bot can connect and communicate with users, in the folder Ava was installed in you should find a file called `confg.example.json`, rename that file to `config.json`, or create a new file called `config.json` and copy the contents of the `config.example.json` file into the new config file and open it using Notepad++ or any other code editor. **Do not edit it with Windows Notepad, that will be a mess.**

Next we'll need to setup a database the Ava can use, Ava requires a database to store things like custom playlists, aliases, channel and server data, and a lot of other things, if you don't have any experiance with `MySQL` databases you can also use `SQLite` which is a lot easier to setup, by default Ava comes with a MySQL database config setup.

If you're planning on using a `MySQL` database you can leave the config as is, if you wanna change to a `SQLite` database setup you can find an example of a [SQLite config setup here](https://gist.github.com/Senither/0f270f8b3579b96c0661c990b3d87fbf), if you're using `SQLite` config example just leave the database parts of the config as is and you should be fine.

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

To start the bot head into the `/scripts` folder, there you'll find a start and update scripts for windows systems, double click on the `windows-start.bat` file and you should be good to go.

If the bot runs without any errors, you have had success so far!

Now you'll need to invite your bot to your server so you can actually use it, take your bots client id from ealier and pop it into a URL like this without the less than and greater than symbols.

    https://discordapp.com/oauth2/authorize?&client_id=<client id>&scope=bot

Just replace the `<client id>` with your actually bot application id, if you don't have your client id you can find it on the [discordapp.com/developers/applications](https://discordapp.com/developers/applications/me) page, just click on your application, the client ID is at the very top under the **App Details** section.

Go to the URL in a web browser, select your server and ht `Authorize`, your bot should now be on your server.

You can test simple functionality by running the ping command in a text channel that the bot can see. If it answers "Pong!", then congratulations, you have successfully set up AvaIre!

Remember to keep the command window open, otherwise the bot will stop running! When you want to stop it, just close the command window.
And that's it! You are now ready to start using your very own AvaIre instance!
Keep in mind, if you have further questions or need help, we're around over at our official server, [AvaIre Central](https://discord.gg/gt2FWER)!

On the behalf of the AvaIre team, we hope you enjoy your bot!
