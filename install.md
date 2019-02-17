# Installing Allium 

To install Allium, run this command in a **Command Computer** with a **Plethora Creative Chat Module**. It's that simple!

```
pastebin run LGwrkjxm
```

The installer installs:

- The Allium Repo - allium.lua, plugins/allium-stem.lua, colors.lua, readme.md

- The Raisin Repo - raisin/raisin.lua, raisin/readme.md

- Apemanzilla's [gitget](http://www.computercraft.info/forums2/index.php?/topic/17387-gitget-version-2-release/), a github repository downloader that is necessary to download Allium, and the plugins that can be installed. 

- repolist.csh - A _Craftos SHell_ file, where you can gitget various plugins and utilities and keep them up to date.

- startup.lua - startup file that runs the repolist file, then runs Allium. When Allium crashes/exits it will reboot after 5 seconds unless interrupted.

- persistence.ltn - A _Lua Table Notation_ file containing all serialized persistence entries for each plugin.

# Installing Plugins

Installing plugins is just as simple as Installing Allium! All you need to do is add some information into the `repolist.csh` file.

The `repolist.csh` file is simply a list of CraftOS commands that are to be executed one after the other. To install a plugin from github for example, since `gitget` is installed by Allium, one could do something like:

```
gitget username plugin_repo commit_hash /plugins/plugin_name
```

Where:
- `username` is the github username of the developer
- `plugin_repo` is the repository on that user's profile where the plugin is located
- `commit_hash` is a safe commit hash to clone from
- `/plugins/plugin_name` is the location where you want to install the plugin

Gitget is not the only method of obtaining plugins, but it is one of the safest. You could also use `pastebin` or `wget` if you so fancy:

```
pastebin get paste_code /plugins/plugin_name
```

Where:
- `paste_code` is the 10 or so digit base-64 pastebin code found at the end of the URL
- `/plugins/plugin_name` is the location you want to install the plugin

```
wget url /plugins/plugin_name
```

Where:
- `url` is the URL of the plugin
- `/plugins/plugin_name` is the location you want to install the plugin

__NOTE 1__ Plugins will only be loaded if they are within the `/plugins` directory. If the plugin is a single file then it is not necessary to install into a seperate directory, but for consistency it's a good idea. Certain plugins may depend on multiple files to execute, it's in this case where a directory is almost always necessary.

__NOTE 2__ There are _MANY_ more ways to install plugins, some could theoretically come with installers that automatically add the entry properly to the repolist. Hell a plugin could probably be developed to handle this! Just remember that these are not the definitive steps to installing the plugin, and it is up to the developer to mention an alternative method should there be one.

# Installing for Devs

In the event that you've made the decision develop a plugin using Allium or admininstrate a server with Allium, there's some pretty important information you'll want to know about.

- On startup, Allium pulls the latest version committed to the master branch. Generally these will be __stable__, non-breaking changes. However, if you don't trust me (I wouldn't), you can always replace `master` with a specific commit hash. This is especially useful for prospective Allium server operators (I can't see a high demand for them...), preventing me from being able to push an update that will `/summon minecraft:creeper` on repeat within your server is generally a good idea. 

- If you're really not liking Allium constantly reinstalling, like myself (many a time did the auto update script overwrite a file), simply create a file in the root directory titled `debug.cfg` and plonk the boolean value `true` into it. This will prevent Allium from repeatedly downloading and further prevent me from pushing updates that will `/tp @a 0 0 0` on repeat from within your precious server.  

- Have a look at the documentation provided in this wiki.

- It's also generally beneficial to be aware of the things that are getting added to Allium before thay're released. If you're interested in that, try cloning the [unstable branch](https://github.com/hugeblank/Allium/tree/unstable-as), or simply change the `repolist.csh` file to pull from the `unstable-as` branch. Documentation on the unstable branch can be found [here](docs/unstable.md)

Warning: If debug mode is enabled it prevents all plugins from updating. Depending on what you're doing this may be undesired behaviour.