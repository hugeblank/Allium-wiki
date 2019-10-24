# Allium Config Layout

Allium's config can be found in `/cfg/allium.lson`. Here's what the default looks like:

    {
        import_timeout = 5,
        label = "<&r&dAll&5i&r&dum&r> ",
        updates = {
            deps = true,
            allium = true
        }
    }

Here are the descriptions for each field:

- `import_timeout`: The maximum amount of time it takes to wait for a plugin dependency to provide its module.
- `label`: The label the loader uses.
- `updates`: Various auto-update configurations. Server operators may want to change these from the default
  - `deps`: Automatically update dependencies
  - `allium`: Automatically update Allium
