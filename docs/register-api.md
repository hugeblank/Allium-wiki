# Register API

The following API is returned from [`allium.register`](allium-api.md), in a table. This is the API provided when you register a plugin.

## Functions

### `command`

Register a command within this plugin

- **Parameters**
  - _string_: command name
  - _function_: function to execute
  - _string_: information about the command __OR__ _table_: info about the command in a table that meets the [info formatting](info-formatting.md) standard
- **Returns**
  - _none_

### `thread`

Register a thread within this plugin

- **Parameters**
  - _function_: function to turn into a thread
- **Returns**
  - _table_: wrapped Raisin thread (see Raisin's thread API [documentation](https://github.com/hugeblank/raisin/wiki))

### `module`

Register an API for this plugin, can only be executed once

- **Parameters**
  - _table_: API to be made external
- **Returns**
  - _none_

### `import`

Request a module from a specific plugin

- **Parameters**
  - _string_: Plugin ID
- **Returns**
  - _table_: The requested plugin module

### `loadConfig`

Generates an LSON configuration file for a plugin

- **Parameters**
  - _table_: default values contained in config (must be serializable)
- **Returns**
  - _table_: sanitized config files with missing entries filled by the default values

### `loadLibs`

Locally save and then load libraries from a URL. Updates library if URL changes and removes it if table entry is removed.

- **Parameters**
  - _table_: libraries to be loaded with the name as the key, and the URL as the value
- **Returns**
  - _table_: loaded libraries with the name as the key, and whatever the library returns as a value

## Other

_magic-table_ `cache`: A [magic table](magic-tables.md) to store anything that the user isn't meant to see
_table_ `update`: A micro-service to hook into Allium's builtin notification system (see [update-service.md])
