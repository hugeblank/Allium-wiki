# Allium API

The following API is loaded on execution of Allium, and placed into the global environment. All functions located here are returned by requiring `allium`. Any references to anything on this page will refer to it by `allium.<name>`. This assumes that the variable allocated for requiring the Allium API is called `allium`.

## Functions

### `assert`

Lua's generic assert, with the ability to set the error level

- **Parameters**
  - _boolean_: condition to test
  - _string_: error message
  - _[number]_: error level + 3 | Default: `3`
- **Returns**
  - _none_

### `sanitize`

Sanitize plugin names to meet Plugin ID standards

- **Parameters**
  - _string_: plugin/command name string
- **Returns**
  - _string_: valid allium plugin/command ID

### `log`

Logs informative messages to the console using the nifty `[I]` tag

- **Parameters**
  - _any_: thing to log
  - _..._
- **Returns**
  - none_

### `warn`

Logs warning alert messages to the console using the nifty `[W]` tag

- **Parameters**
  - _any_: thing to warn
  - _..._
- **Returns**
  - none_

### `tell`

Output [formatted](color-formatting.md) text

- **Parameters**
  - _string_: name of user
  - _string_: text __OR__ _table_: list of text
  - _[string]_: label replacement __OR__ _[boolean]_: hide label
- **Returns**
  - _string_: execution results

### `execute`

Execute a command as a player

- **Parameters**
  - _string_: Username of target
  - _string_: Command to execute with parameters
- **Returns**
  - _none_

### `getPlayers`

Lists all online players

- **Parameters**
  - _none_
- **Returns**
  - _table_: list of online players

### `getPosition`

Gets the position, dimension, or rotation of a player or entity

- **Parameters**
  - _string_: name or UUID of player/entity
- **Returns**
  - _table_: Table containing a `position` table (where indices 1, 2, and 3 correspond to x, y, and z), a `rotation` table (where indices 1 and 2 correspond to x and y rotation), and a `dimension` number (where 0 is overworld, -1 is nether, and 1 is the end)

### `getInfo`

Get information data for one or all plugins

- **Parameters**
  - _[string]_: allium plugin ID
- **Returns**
  - _table_: table of information organized as `table[plugin][command] = information`

### `getName`

Get the human readable name from the plugin ID

- **Parameters**
  - _string_: allium plugin ID
- **Returns**
  - _string_: human readable plugin name

### `forEachPlayer`

Perform an operation on each player

- **Parameters**
  - _function_: function containing operations. Receives the username as a string parameter.
- **Returns**
  - _boolean_: operation result
  - _string_: error if the operation failed

### `register`

Register an Allium plugin

- **Parameters**
  - _string_: plugin name, converted to allium plugin ID
  - _string_: semver string
  - _[string]_: optional manually set human readable plugin name
- **Returns**
  - _table_: list of functions, see [Register API](register-api.md)

### `verify`

Takes in a range of versions (`>= 0.7.0 && < 1.0.0`), comparison of a version (`> 1.12.3`), or an expicit version (`1.1.2`) to put against the current Allium version. All versions must be [SemVer](https://semver.org) compliant.

- **Parameters**
  - _string_: version comparison operation
- **Returns**
  - _boolean_: true when Allium's version meets the criterea

### `getVersion`

Get the SemVer table of a plugin

- **Parameters**
  - _string_: plugin ID
- **Returns**
  - _table_: parsed SemVer table, see [SemParse](https://github.com/hugeblank/semparse)

---

## Events

### `player_join`

Fired when a player joins
**Parameters**

- _string_ username

### `player_quit`

Fired when a player leaves
**Parameters**

- _string_ username

---

## Other

_string_ `side`: The location of the chat recorder that allium is using
_table_ `version`: Allium's current version, parsed as a SemVer table
