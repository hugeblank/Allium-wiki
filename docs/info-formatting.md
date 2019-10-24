# Info Formatting

Command information is the third argument of a command to be registered. All commands require that some sort of detail about their functionality be provided on registering, in general this information provides the user a brief explanation of the commands purpose. This page covers how Allium makes documenting commands anything but a chore.

## Simple Formatting

The easy way out...

Simple Formatting is one of two methods of providing information about your command. Providing a sentence or two describing the purpose of the command as a string into the info argument is enough. For example, `allium:plugin` does just this by providing a simple help string: "Lists the name of all plugins installed on allium".

This method of formatting is only recommended in the event that your command has no parameters. Developing an advanced command calls for more complex formatting, see below.

## Complex Formatting

Don't let the name fool you, it's called complex because simple was taken...

When we want to provide a more rich experience with our plugins, feeding in a table with information on every path/parameter the command can take is the way to go. In order to properly demonstrate this novel concept, it would be best to use a command that you're already familiar with, `allium:help`. Let's start by looking at its information table:

### Example

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

### Formatting options

Now that we have an example let's break down what's going on:

- `["1"]` is the string that provides a description of what the purpose of the parameter is. Every parameter/field is required to have one, even the command itself. If you're unfamiliar with how tables in Lua work, not providing an index will assume a numerical index, meaning that by leaving a string without an index in a table filled with them will make it index `["1"]`.
- `optional` is for when you want the parameter to be identified as optional. Optional parameters have square brackets around them in the UI. For example, the 'page' parameter for Allium's help command is always optional no matter where.
- `clickable` is for when you want/don't want the parameter to be placed into the suggestion bar and run the next parameter query. The default value is `true`. It is not mandatory to add this unless you specifically don't want the parameter to be clickable. For example, if the 'page' parameter was clickable and the user clicked on it, the word 'page' would be appended. In the scenario that this is undesired, we simply set clickable to false.
- `infill` is for when you want to present a preset variety of options that at the time of running the command you don't know. These could be anything from users to commands, to your own options. `infill` takes a variety of inputs:
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

![comprehensive list of plugins](https://i.postimg.cc/fyzS4nTq/help-plugin.png)

If we click on `plugin:command` instead of `plugin`, we get to select from all of the current commands:

![comprehensive list of commands](https://i.postimg.cc/hPGQpBYf/help-command.png)

Let's click on `!allium:help`:

![parameters being filled in](https://i.postimg.cc/0jVMPWzk/help-select.png)

After we've selected that it puts it into our suggestion clickable within the UI and we can simply hover over it and then click!

![woo!](https://i.postimg.cc/HWz7wxBq/help-suggest.png)

This is the same command we used to get started. In the situation that you wanted to continue in an infinite help loop, keep clicking! :P
