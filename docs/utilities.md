# Utilities
All of these utilities are guaranteed to be present in the directory `lib/`, as of version 0.6.0. Click on the Utility name to go to its source.
## APIs
APIs that can be required by a plugin by calling `require(lib.x)`, where x is one of the following:

- [`nap`](https://github.com/hugeblank/tree/master/qs-cc/src/nap.lua): Translates typical Lua API calls into a REST API URL.
- [`semver`](https://github.com/hugeblank/semparse): Parses a valid semver version string into an object with comparison metamethods.
- [`json`](https://github.com/rxi/json): Encodes/Decodes JSON to Lua tables.
- [`raisin.raisin`](https://github.com/hugeblank/raisin): Thread managment API used significantly in Allium itself. 

## Software
Entries here are various software to help manage installation and managment of Allium, run by typing `/lib/x` into the shell, where x is one of the following:

- [`gget`](https://github.com/hugeblank/tree/master/qs-cc/src/gget.lua): Command line util to install github repositories.