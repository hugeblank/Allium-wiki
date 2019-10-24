# Unstable

Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...

Allium 0.9.0 is in the works! There's a lot to cover...

## Mod Compatability

Introducing Allium Peripherals! I made a mod for 1.14 Fabric that adds a Chat modem, and Creative chat modem that behave identically to Plethora's. It should be as simple as installing CC:Tweaked for Fabric, Fabric API, and Allium Peripherals. Place a command computer down, chat modem on top and you'll be good to go!

### CurseForge Links

- [Allium Peripherals](https://www.curseforge.com/minecraft/mc-mods/allium-peripherals/)
- [CC: Tweaked for Fabric](https://www.curseforge.com/minecraft/mc-mods/cc-tweaked-fabric)
- [Fabric API](https://www.curseforge.com/minecraft/mc-mods/fabric-api)

## Depman Move

Allium's depman instance & listing has been moved to its own GH repo! This all so that in the event that you want to contribute/fork Allium it's much easier. Check the repo out [here](https://github.com/hugeblank/allium-depman)

## Features in Production

[roger109z](https://github.com/roger109z) and I have been spending a bit of time working on minor tweaks, additions and improvements for this version of allium. Here's the list.

### The List

#### Done

- Cleaned up code, removed duplicate config checks between startup and allium
- Added allium.loadConfig when provided a table of values parses a generated config file the user has the ability to modify
- Added .lson extension where needed
- Fix plugin code cleanup
- Added 'position' infill method.

#### To Do

- Revisit color.lua
