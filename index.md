# Welcome

Welcome, traveller, to the Allium wiki!

## What is Allium

I suppose you're here because you have no idea what you're doing so the best way to start would be to explain _what_ exactly Allium is. Allium is a Lua plugin loader for ComputerCraft. Generally, plugins can be considered as server-side mods. This means that you only need the plugins to exist within the server, the client doesn't need to modify their game to join the server. Allium allows for plugins to be loaded in Lua, with the provided API.

At this point you probably want to install Allium. Let's [get started](install.md)!

## Why Allium

Now comes the question, why does Allium even exist? You have to install ComputerCraft and a chat peripheral mod that behaves like [Plethora](https://github.com/SquidDev-CC/Plethora)s creative chat module in order to join a server with Allium on it, so what's the point? My answer to that is simply, java can be excessive. It's a very advanced language with many concepts that are hard to grasp. To make a plugin you need to not only understand Java, but also the API library that the plugin loader provides, which could be huge. This could be very ominous for someone that just wants to develop a plugin that does a simple task like teleport a player around. Enter Allium. Allium uses ComputerCraft (Lua 5.1), which is significantly easier to learn, due to it being a much higher level language than Java. Along with that, the API for Allium is very simple and easy to understand, consisting of only a few methods, all existing within this wiki. It's worth arguing that the ease of use and functionality of Allium outweigh the requirement of having two (three if running on fabric) mods on all clients. It's not that hard to install them, and if you're going to be adding two to three mods, why not add more? Allium can be seen as an encouragment to utilize the mods the community has to offer. Conversely, the modding community can be seen as an encouragmentto utilize Allium!

### Compatible Peripheral mods

- [Plethora Peripherals](https://github.com/SquidDev-CC/Plethora) For Forge (Currently not available for the latest version of the game [which Allium runs in so... yeah.])
- [Allium Peripherals](https://github.com/hugeblank/allium-peripherals) For Fabric

## Allium's History

Let's all flash back to December 2017. I was one of the administrators for Kaos Network, creators of various Minecraft servers including NexCore, Acora, Shinexus, and Project BETA. Project Beta 2 had been released, and was off to a moderate start. One of my admin friends, [Roger](https://github.com/roger109z), slapped together a program using a Command Computer and [Computronics](https://wiki.vexatos.com/wiki:computronics) Chat Box that got user input, put it through a conditional, and then gave an output. After a back and forth debate about the future of the project some time in January 2018, I decided to fork it, and transform it into a plugin loader. I called this plugin loader BagelBot (for obvious reasons), and separated the conditional into its own plugin, BetaBot (since it was used purely for Project Beta). Unfortunately at the time of writing BagelBot I was not as versed in Lua as I am a year later (January 2019). It ended up falling short in almost all regards, it wasn't user friendly, and it definitely wasn't developer friendly. It suffered from a particular bug with persistence, and the plugin structure was janky at best. Almost exactly one year later, on January 19, 2019 I picked BagelBot back up with the intent of restructuring it. I had completed work on [Raisin](https://github.com/hugeblank/raisin), the thread manager I designed with the intent to use in this project. I knew much more about Lua than before, and I was able to successfully rewrite the bot. 5 days later I pushed the first commit "[The Next Generation](https://github.com/hugeblank/Allium/tree/bf62557f2fa6add8c1a30481f417347e31eec12e)", which is the starting point for Allium.
