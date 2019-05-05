# Unstable

Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...

## 🦀 1.12 is gone! 🦀

As of 0.7.0-pr0 Allium *functions in 1.13.2. Which is the only version that forge currently supports, so from now on any mention of Allium's support, we will just call 1.13.

### Changes

#### Improvements

Here's what's been going on for the past 2 weeks:

- Allium now has to be required in your plugin files. This allows for better modularity, and now you can rest easy knowing that nobody can overwrite it.
- Infill tags now don't have a weird space in them. `this= that` is now `this=that` and this is how that should have been all along.
- After a 2 week break I used to relax and have a thunk about how to manage the clutter that the dependency list was becoming, I created depman. Depman allowed for me to have fine control over all of the dependencies for all versions of Allium while also not having to be tied to the Allium repository. Now it's as simple as me adding an entry to a serialized Lua table on pastebin. [Check it out!](https://pastebin.com/fisfxn76)
- Depman allowed me to also work on creating some of my own libraries for the project. The first and only thus far is my MoJSON parser. Mojang decided to loosely abide by the formatting standards of JSON, while also making their own. This wouldn't really have mattered to Allium if it weren't for the beautiful `/data` command, which allows for getting the position and even the dimension of the player. Thus, [MoJSON](https://github.com/hugeblank/qs-cc/blob/377de7135a291a9a3b79e01034432389295f45b9/src/allium/mojson.lua).
- All dependencies are now located strictly in `/lib`, thanks to Depman.
- Added a configuration file that's much more straightforward than a little file floating around called `debug.cfg`.
- _Lua Table Notation_ was what I called all files containing a serialized Lua table entry, until now. It has been arbitrarily decided ([read](https://discordapp.com/channels/198130613759246337/198142140805677065/573418446235107328)) that _Lua Serialized Object Notation_ should be the standard name. All files have been updated to follow this convention.
- `verify` now checks for equality if you only feed in one version string.
- 🦀 `getPosition` is back! 🦀 And for good! As mentioned above, MoJSON allows for getting the position and dimension of the player. getPosition does this. Read on for more direct documentation on API features.

#### API

Here's everything boiled down to what matters for the developer, the documentation:

##### `verify`

Compares two SemVer strings to the Allium version, or checks the equality of one

- **Parameters**
  - _string_: minimum version or version to check the equality of
  - _[string]_: maximum version
- **Returns**
  - _boolean_: true when the min version exists and is *lt* Allium's version and the max version exists and is *gt* Allium's version. If a single version was given, returns true if the versions were equal, false otherwise.

##### `getPosition`

Gets the position, dimension, or rotation of a player or entity

- **Parameters**
  - _string_: name or UUID of player/entity
- **Returns**
  - _table_: Table containing a `position` table (where indices 1, 2, and 3 correspond to x, y, and z), a `rotation` table (where indices 1 and 2 correspond to x and y rotation), and a `dimension` number (where 0 is overworld, -1 is nether, and 1 is the end)