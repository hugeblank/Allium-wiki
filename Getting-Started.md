Let's get you into the realm of Allium!

## Installation
To install Allium, run this command in a **Command Computer** with a **Plethora Creative Chat Module**. It's that simple!

`pastebin run LGwrkjxm`

The installer installs:

- The Allium Repo - allium.lua, plugins/allium-stem.lua, colors.lua, readme.md

- The Raisin Repo - raisin/raisin.lua, raisin/readme.md

- Apemanzilla's [gitget](http://www.computercraft.info/forums2/index.php?/topic/17387-gitget-version-2-release/), a github repository downloader that is necessary to download Allium, and the plugins that can be installed. 

- repolist.csh - A _Craftos SHell_ file, where you can gitget various plugins and utilities and keep them up to date.

- startup.lua - startup file that runs the repolist file, then runs Allium. When Allium crashes/exits it will reboot after 3 seconds unless interrupted.

- persistence.ltn - A _Lua Table Notation_ file containing all serialized persistence entries for each plugin.

## Developing

Developers for Allium may want to take a look at the documentation provided in this wiki, in no particular order:
- [Formatting Codes](https://github.com/hugeblank/Allium/wiki/Formatting-Codes)
- [Allium API Documentation](https://github.com/hugeblank/Allium/wiki/Allium-API)
- [Register API Documentation](https://github.com/hugeblank/Allium/wiki/Register-API)
- [Command Parameter Documentation](https://github.com/hugeblank/Allium/wiki/Command-Parameter)
As a developer you may also want to take a look at some of the things that are getting added to Allium before thay're released. If you're interested in that, try cloning the [unstable branch](https://github.com/hugeblank/Allium/tree/unstable-as). Documentation on unstable functions can be found [here](https://github.com/hugeblank/Allium/wiki/Unstable)