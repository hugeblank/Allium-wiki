# Info Formatting

Command information is the third argument of a command to be registered. All commands require that some sort of detail about their functionality be provided on registering, in general this information provides the user a brief explanation of the commands purpose. This page covers how Allium makes documenting commands anything but a chore.

## Simple formatting

The easiest method of formatting information is by providing a string:

```
local plugin = allium.register("foo") -- Register plugin "Foo"

local function bar(name, args, meta) -- Define a function to be used in command "bar"
    if args[1] == "test" then -- If the first argument is "test"
        allium.tell("@a", name.." said test") -- Announce the user tested
    elseif args[1] == "poke" then -- If the first argument is "poke"
        local players = allium.getPlayers() -- Get a list of players
        for i = 1, #players do -- For each player
            if players[i] == args[2] then -- Check if the player to poke exists
                allium.tell(args[2], "POKE! ~"..name) -- Poke, and mention who poked them
                return -- Return out of command
            end
        end
        allium.tell(name, "You POKED yourself!") -- The player didn't exist, so the poke hits the poker
    else -- If the first argument was neither "test" nor "poke"
        local players = allium.getPlayers() -- Get a list of players
        for i = 1, #players do -- For each player
            if players[i] == args[1] then -- If the player is online
                allium.tell(args[1], name.." is thinking about you <3") -- Snitch about a crush
                return -- Return out of command
            end
        end
        meta.error() -- Give the usage if the player wasn't online
    end
end

plugin.command("bar", bar, "Does random stuff like poking users") -- Define command "bar"
```

The result, nothing too shocking:

![](https://drive.google.com/uc?export=view&id=1GiP8IQBWamVYy1AxwCKgC1DjBe7t07uY)

In this example we define a command `bar`, and simply give a string declaring it's purpose. This is fine and dandy for smaller commands that take in little to no parameters, but in this `bar` command, there's too much going on for a single string to properly describe. Sure we could write multiple sentences on this command, but information is supposed to be a short overview, not a monologue.

## Advanced formatting

Enter the info table. Here we use the same example from above, but instead of adding a string into the info parameter, we put in a table that is defined above the function and command.

```
local plugin = allium.register("foo") -- Register plugin "Foo"

local bar_info = { -- Create an information table
    "Demo command that does some stuff", -- general purpose of the command
    test = { -- One of the parameters
        "Tells the world you said test" -- Purpose of the parameter
    },
    poke = { -- Another one of the parameters
        "Pokes someone, or yourself if you really want to", -- Purpose of this parameter
        name = { -- A field within this parameter
            optional = true, -- This field is optional, meaning it can be left blank
            "Name of the user you would like to poke" -- Purpose of this field
        }
    }
    name = { -- Final parameter option
        noclick = true, -- Ensure this cannot be used for autofill (will be explained below)
        "Name of a user you're thinking about" -- Purpose of this parameter
    }
}

local function bar(name, args, meta) -- Define a function to be used in command "bar"
    if args[1] == "test" then -- If the first argument is "test"
        allium.tell("@a", name.." said test") -- Announce the user tested
    elseif args[1] == "poke" then -- If the first argument is "poke"
        local players = allium.getPlayers() -- Get a list of players
        for i = 1, #players do -- For each player
            if players[i] == args[2] then -- Check if the player to poke exists
                allium.tell(args[2], "POKE! ~"..name) -- Poke, and mention who poked them
                return -- Return out of command
            end
        end
        allium.tell(name, "You POKED yourself!") -- The player didn't exist, so the poke hits the poker
    else -- If the first argument was neither "test" nor "poke"
        local players = allium.getPlayers() -- Get a list of players
        for i = 1, #players do -- For each player
            if players[i] == args[1] then -- If the player is online
                allium.tell(args[1], name.." is thinking about you <3") -- Snitch about a crush
                return -- Return out of command
            end
        end
        meta.error() -- Give the usage if the player wasn't online
    end
end

plugin.command("bar", bar, bar_info, "<test | poke | name> [name]") -- Define command "bar"
```

The result, much better:

<img src="https://drive.google.com/uc?export=view&id=1iTE3RRG0cYaDJ4oWG-3sxF6GX1zbGSHw" alt="info-table" style="width:100%;"/>

Using the same example from above we simply add a table that lists out each parameter and field and end up creating a structure that accurately represents nearly all possible inputs of the command. This is really powerful, not just because it enables significantly more readability, but we could actually use this same table to autofill and populate the chat interface for the user. 

<img src="https://drive.google.com/uc?export=view&id=1bShmIGd4CA2DMYZlfa2VOdQ83mQR0-qj" alt="info-table" style="width:100%;"/>

## Parameter States

The display shown above also allows us to tell the user which parameters are required, and which are optional. Parameters that are required in a command are marked with the greater than and less than symbols, `<like so>`, while parameters that can be omitted are marked with square braces `[like so]`. Parameters that are required do not need any special formatting in the information table, but optional parameters need a flag `optional` to be set to true. In the above example, the 'name' field in the 'poke' parameter has the optional flag set. The `optional` flag disables the ability to autofill up to that point, giving the user the freedom to utilize it or not. The final parameter variant is a blend of the two parameter types so far discussed. These are required parameter types that need a special input, like a username. To prevent autofill from filling in a parameter that requires user input, the `noclick` flag can be set. In the example above, the lowest 'name' parameter has the `noclick` flag set.