# Update Micro-service

The following methods are found within the `update` table of a registered plugin. These methods are used to hook into Allium's user-friendly update notification and execution system. Hooking into the update service is totally optional and not required to make a plugin.

## Functions

### `setMethods`

Set the methods that this plugin uses to update

- **Parameters**
  - _function_: function to check whether there is an update available, should return `true` or `false`
  - _function_: function to execute the update
- **Returns**
  - _none_

## Other

_magic-table_ `cache`: A [magic table](magic-tables.md) to store critical information to the update service
_table_ `default`: Common update methods for various platforms plugins may ship on. See below.

## Defaults

### `github`

Returns a checker and runner that pull from github repos. It expects the following keys in the update cache:

- `user`: github username
- `repo`: repository name
- `branch`: branch or tag name
- `[path]`: optional path (prepends the `plugins` directory automatically)

- **Parameters**
  - _none_
- **Returns**
  - _function_: checker function
  - _function_: runner function

### `pastebin`

Returns a checker and runner that pull from pastebin. It expects the following keys in the update cache:

- `id`: github username
- `path`: path with filename (prepends the `plugins` directory automatically)
