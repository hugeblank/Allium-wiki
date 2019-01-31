Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...

## General Information
  - A scanner thread has been added which emits 2 events:
    - (`player_join`, _string_ username): Fired when a player joins
    - (`player_quit`, _string_ username): Fired when a player leaves

## `allium`
Functions found within the `allium` global:
#### getPosition: Get the position of a player
- **Parameters**
  - _string_: Username of target
- **Returns**
  - _number_: x coordinate of player
  - _number_: y coordinate of player
  - _number_: z coordinate of player

#### forEachPlayer: Perform an operation on each player
- **Parameters**
  - _function_: function containing operations. Receives the username as a string parameter.
- **Returns**
  - _boolean_: operation result
  - _string_: error if the operation failed

## `register`
Functions found within the `allium.register` return table:
#### `thread`: Register a thread within this plugin
- **Parameters**
  - _function_: function to turn into a thread
- **Returns**
  - _table_: wrapped Raisin thread (see Raisin's thread API [documentation](https://github.com/hugeblank/raisin/wiki)) 
This change (^) was the intended behaviour.