# Command Parameters

As a plugin developer several tools and utilities are provided to make programming with Allium that much easier. As you hopefully already know from reading the [Register API Documentation](register-api.md), registering a command takes in a function. When that function is executed it is given a few arguments:

`command = function(name, arguments, data)`

- _string_: name of the user that invoked the command
- _table_: arguments provided after the invocation (Eg: `!help allium 2` arguments: `{"allium", "2"}`)
- _table_: list of seldom used, but useful items related to command usage
  - `error` _function_ | Quick and easy way to return command usage, or other information to the executor
    - **Parameters**
      - _[string]_: error message | Default: An automatically created command usage string, generated from the command information
    - **Returns**
      - _none_
  - `uuid` _string_ | Provides the UUID of the user that called the command

---

Parameters that have quotes around them get added into the command argument table as one index. So, something like:

    !democommand argument1 "argument number two"

would be parsed to look like:

    {
      "argument1",
      "argument number two"
    }