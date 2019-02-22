Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...

## Allium API
`sanitize` had a functionality tweak, only accepts (lowercase) alphanumeric and '_'
#### `execute`
Execute a command as the player

- **Parameters**
 - _string_: Username of target
 - _string_: Command to execute with parameters
- **Returns**
 - _none_

## Register API
`.require` has been renamed to `.import` as requested in [#15](https://github.com/hugeblank/Allium/issues/15).

## Information Formatting Overhaul
That's right! Information formatting has finally reached an acceptable form. Check it out!

### Example
```
help = {
    "This command! Helpful",
    page = {
        optional = true,
        clickable = false,
        "Page number to display"
    },
    plugin = {
        optional = true,
        infill = "plugin",
        "Specific plugin to list commands for",
        page = {
            optional = true,
            clickable = false,
            "Page number to display"
        }
    },
    ["plugin:command"] = {
        optional = true,
        infill = "command",
        "Specific command to list arguments for",
        page = {
            optional = true,
            clickable = false,
            "Page number to display"
        }
    }
}
```

### Formatting options
There's a lot going on, let's break it down:
- `optional` is for when you want the parameter to be identified as optional. Optional parameters have square brackets around them in the UI. For example, the 'page' parameter for Allium's help command is always optional no matter where.
- `clickable` is for when you want/don't want the parameter to be placed into the suggestion bar and run the next parameter query. The default value is `true`, it is not mandatory to add this unless you specifically don't want the parameter to be clickable. For example, if the 'page' parameter was clickable and the user clicked on it, the word 'page' would be appended. This is undesired, so we set clickable to false.
- `infill` is for when you want to present a preset variety of options that at the time of running the command you don't know. These could be anything from users to commands, to your own options. Infill takes a variety of inputs:
    - `"username"`: Generates a UI listing all of the online users
    - `"plugin"`: Generates a UI listing all of the plugins that got successfully loaded
    - `"command"`: Generates a UI listing all of the commands with their plugin name prefix. This does not prepend an '!' to the command.
    - `table`: Takes a table of strings and converts it to a list of options for the user.
    - `function`: Runs a function provided to get a table of strings. Converts this table in the same manner that the table option above does
Infills provide a dynamic capability to your command that is nigh on uncomparable to Minecraft's own vanilla functionality. An example of this can be found in Allium's help command 'plugin' and 'plugin:command' parameters. 'plugin' simply uses an infill to list the plugins loaded, and 'plugin:command' lists all commands.
- `default` is for when you don't necessarily want an infill for a parameter, but would like it to provide _something_

### User Interface
Now putting all of this together we get a comprehensive UI of the help command. If we test this by running `!allium:help allium:help` we see this:

![ooh!](https://i.postimg.cc/NM72PfYr/help.png)

On the top in red within the UI is the command. If we click on it the text there will be placed in our chat input so that all we have to do is press enter.

If we click on the `plugin` option we get presented with the list of plugins, which happen to show allium's stem plugin, and a couple of other plugins I have in my workspace:

![comprehensive list of plugins!](https://i.postimg.cc/fyzS4nTq/help-plugin.png)

If we click on `plugin:command` instead of `plugin`, we get to select from all of the current commands:

![comprehensive list of commands!](https://i.postimg.cc/hPGQpBYf/help-command.png)

Let's click on `!allium:help`:

![parameters being filled in!](https://i.postimg.cc/0jVMPWzk/help-select.png)

After we've selected that it puts it into our suggestion clickable within the UI and we can simply hover over it and then click!

![woo!](https://i.postimg.cc/HWz7wxBq/help-suggest.png)

This is the same command we used to get started so in the situation that you wanted to continue in an infinite help loop, keep clicking! :P

## Quoting Parameters
I decided to make this a seperate heading from the above because it's less focused on the stem plugin and more on how Allium interprets arguments. The gist of it is parameters that have quotes around them get added into the command parameter argument table as one index. The twist is the quote can be in the middle of an argument. For example: 

```param1 param2-"is now this quoted stuff and 'param2-'."```

The first argument is simply "param1", but the second argument is _all_ of the remaining text. This may seem counterintuitive but it adds some pretty neat features. The help command would be difficult to implement without this. 

^ I take this back, it will be unimplemented in the next unstable patch. Quotes will behave less quirky.

