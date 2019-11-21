# Magic Tables

Magic tables behave almost identical to tables with the added feature that the data they contain persists after reboot. Every value changed, added, or removed is handled in an external file.

## Iterating

This is the one and only difference between regular tables, and magic tables. In order to properly save the state of the table iterating through it has been made slightly more difficult. Slightly in that you only have to type two more characters in than usual.

Let's say you have a setup like this in `myplugin.cache.nums`:

    nums = {
        1,
        2,
        3
    }

And for whatever reason you want to iterate through it. Here's what you would do:

    for i = 1, #myplugin.cache.nums() do
        allium.log(myplugin.cache.nums[i])
        myplugin.cache.nums[i] = i+1
    end

The eagle-eyed may have caught that we're _calling_ the index, which you don't (and can't) do to a regular table. Calling any index will return the raw table so that the size can actually be attained. The same applies for when you want to get key-value pairs from a table. When you pass it to `pairs`, `ipairs` or the like, you need to call it first.

Note: It's a bad idea to store called magic tables. They are literally just the regular table that the magic table is based off of and have none of the persistent properties that magic tables do.
