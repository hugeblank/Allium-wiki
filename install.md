# Installation Guides

## Installing Allium

To install Allium, run this command in a **Command Computer** with a **Plethora Creative Chat Module**. It's that simple!

    pastebin run LGwrkjxm [path]

- `[path]`: Optional path to place Allium

Note: This method only functions for the latest version of Allium. If you need a legacy version of Allium for whatever reason, install a repo downloader like [`gitget`](https://pastebin.com/W5ZkVYSi) by Apemanzilla, or my `gget` and install the tagged version

The installer installs all the following in the selected path (defaults to `/`):

- `allium.lua`: The plugin loader herself
- `startup.lua`: Initializer script used to run Allium
- `plugins/`: Directory to place all plugins
  - `allium-stem.lua`: Core Allium plugin, provides basic commands
- `cfg/`: Directory for all config files
  - `allium.lson`: Config options for Allium that can be changed by the administrator
  - *`dependencies.lson`: Dependency data meant for the Depman instance
  - *`persistence.lson`: Plugin data intended to persist over restarts
  - *`version.lson`: Information about the current version of Allium
- `lib/`: Directory for all utilities, listed [here](docs/utilities.md)

Note: Files that have a * before them are not meant to be modified by you, the user. Touching them could cause unexpected behavior that I, or anyone else that contributes to this project are responsible for. You have been warned.

## Installing Plugins

Installing plugins is just as simple as Installing Allium!

To install a plugin from github for example, use `gget`. `gget` is installed by Allium in the `lib` directory. It allows you to install an entire plugin directly from the command line, like so:

    /lib/gget username plugin_repo branch /plugins/plugin_name

Where:

- `username` is the github username of the developer
- `plugin_repo` is the repository on that user's profile where the plugin is located
- `branch` is a safe commit hash/tag/branch to clone from
- `/plugins/plugin_name` is the location where you want to install the plugin

Gget is not the only method of obtaining plugins, but it guarantees you're getting all the files. You could also use `pastebin` or `wget` for single file plugins. For `pastebin`:

    pastebin get paste_code /plugins/plugin_name

Where:

- `paste_code` is the 10 or so digit base-64 pastebin code found at the end of the URL
- `/plugins/plugin_name` is the location you want to install the plugin

And for `wget`:

    wget url /plugins/plugin_name

Where:

- `url` is the URL of the plugin file
- `/plugins/plugin_name` is the location you want to install the plugin

Tip: Plugins will only be loaded if they are within the `/plugins` directory. If the plugin is a single file then it is not necessary to install into a seperate directory, but for consistency it's a good idea. Certain plugins may depend on multiple files to execute, it's in this case where a directory is almost always necessary.

## Operating as a Dev/Admin

In the event that you've made the decision develop a plugin using Allium or admininstrate a server with Allium, there's some pretty important information you'll want to know about.

- Allium automatically checks for dependency and Allium updates. If there are any, an informative message (or three) will pop up explaining what's available for updating. Along with that, in like with the 3 exit buttons on the bottom right of your screen, a blue button with an arrow will pop up. At this point it's up to you to make sure that all plugins function in the latest version. Generally, having a backup before you update is a good idea.

- If you're getting annoyed by allium alerting you that there's an update, check out the [Allium config](docs/config-layout.md). It provides options to disable update notifications from Allium, the depedency managment software, and plugins.

- Have a look at the documentation provided in this wiki.

- It's also generally beneficial to be aware of the things that are getting added to Allium before thay're released. If you're interested in that, take a look at the Documentation, found here [here](docs/unstable.md). If anything there intrigues you, take a look at the [unstable branch](https://github.com/hugeblank/Allium/tree/unstable-as), or even redirect your Allium by changing the `updates.repo.branch` config option to `"unstable-as"`.

Warning: Unstable *means* unstable. Breaking changes are a thing that happen constantly in that branch and are often a pain in the rear to work out. If you really want to do this you should probably have a knowledge of the inner workings of Allium.
