# Utilities

All of these utilities are guaranteed to be present in the directory `lib/`, as of version 0.6.0. Click on the Utility name to go to its source.

## APIs

APIs that can be required by a plugin by calling `require("lib.x")`, where x is one of the following:

- [`color`](https://github.com/hugeblank/qs-cc/blob/master/src/allium/color.lua): color parsing library used in [`allium.tell`](allium-api.md#tell).
- [`nap`](https://github.com/hugeblank/qs-cc/blob/master/src/nap.lua): Translates typical Lua API calls into a REST API URL.
- [`semver`](https://github.com/hugeblank/semparse): Parses a valid semver version string into an object with comparison metamethods.
- [`json`](https://github.com/rxi/json.lua): Encodes/Decodes JSON to Lua tables.
- [`raisin`](https://github.com/hugeblank/raisin): Thread managment API used significantly in Allium itself.
- [`mojson`](https://github.com/hugeblank/qs-cc/blob/master/src/allium/mojson.lua): Encodes/Decodes Mojang's NBT format (MoJSON) to Lua tables.

## Software

Entries here are various software to help manage installation and managment of Allium, run by typing `/lib/x` into the shell, where x is one of the following:

- [`depman`](https://github.com/hugeblank/qs-cc/blob/master/src/depman.lua): Dependency Managment utility used by Allium. Specific instance used is located [here](https://github.com/hugeblank/allium-depman/)
- [`gget`](https://github.com/hugeblank/qs-cc/blob/master/src/gget.lua): Github Repository installer
