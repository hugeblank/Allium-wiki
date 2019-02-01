The following API is returned from [`allium.register`](https://github.com/hugeblank/Allium/wiki/Allium-API), in a table. 

## Functions:
#### `command`
Register a command within this plugin
- **Parameters**
  - _string_: command name
  - _function_: function to execute
  - _string_: information about the command
  - _[string]_: command usage formatted as `<required | first | arguments> [optional | second | arguments]`
- **Returns**
  - _none_

#### `thread`
Register a thread within this plugin
- **Parameters**
  - _function_: function to turn into a thread
- **Returns**
  - _table_: wrapped Raisin thread (see Raisin's thread API [documentation](https://github.com/hugeblank/raisin/wiki))

#### `setPersistence`
Sets data that will remain persistent across a reboot of Allium.
- **Parameters**
  - _string_: name of the persistent value
  - _any_: data to assign to value
- **Returns**
  - _none_

#### `getPersistence`
Sets data that will remain persistent across a reboot of Allium.
- **Parameters**
  - _string_: name of the persistent value
- **Returns**
  - _any_: data that was assigned to that value
---
Read Next: [Command Parameter Documentation](https://github.com/hugeblank/Allium/wiki/Command-Parameter)