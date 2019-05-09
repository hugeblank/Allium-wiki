# Register API

The following API is returned from [`allium.register`](docs/allium-api.md), in a table. This is the API provided when you register a plugin.

## Functions

### `command`

Register a command within this plugin

- **Parameters**
  - _string_: command name
  - _function_: function to execute
  - _string_: information about the command __OR__ _table_: info about the command in a table that meets the [info formatting](docs/info-formatting.md) standard
- **Returns**
  - _none_

### `thread`

Register a thread within this plugin

- **Parameters**
  - _function_: function to turn into a thread
- **Returns**
  - _table_: wrapped Raisin thread (see Raisin's thread API [documentation](https://github.com/hugeblank/raisin/wiki))

### `module`

Register an API for this plugin

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

### `setPersistence`

Sets data that will remain persistent across a reboot of Allium.

- **Parameters**
  - _string_: name of the persistent value
  - _any_: data to assign to value
- **Returns**
  - _none_

### `getPersistence`

Sets data that will remain persistent across a reboot of Allium.

- **Parameters**
  - _string_: name of the persistent value
- **Returns**
  - _any_: data that was assigned to that value