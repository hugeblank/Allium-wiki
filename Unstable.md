Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...

## General Information
  - Tables of functions called 'modules' have been added for better plugin to plugin interaction, see below for more info on their function.

## `allium`
Functions found within the `allium` global:
#### require
Locally load a module
- **Parameters**
  - _string_: Name of plugin to load module from
- **Returns**
  - _table_: module of target plugin
## `register`
Functions found within the `allium.register` return table:
#### `module`
Register a module API within this plugin
- **Parameters**
  - _table_: plugin API
- **Returns**
  - _none_
