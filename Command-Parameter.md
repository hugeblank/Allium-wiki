As a plugin developer several tools and utilities are provided to make programming with Allium that much easier. As you hopefully already know from reading the [Register API Documentation](https://github.com/hugeblank/Allium/wiki/Register-API), registering a command takes in a function. When that function is executed it is given a few arguments:

#### `command = function(name, arguments, data)`
  - _string_: name of the user that invoked the command
  - _table_: arguments provided after the invocation (Eg: `!help allium 2` args: `{"allium", "2"}`)
  - _table_: list of seldom used, but useful items related to command usage
    - `error` _function_ | Quick and easy way to return command usage, or other information to the executor
      - **Parameters**
         - _[string]_: error message, if left nil uses the command usage string
      - **Returns**
        - _none_
    - `usage` _string_ | Provides raw access to the usage string for the command