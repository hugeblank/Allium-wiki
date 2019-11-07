# Allium Config Layout

Allium's config can be found in `/cfg/allium.lson`. Here's what the default looks like:

    {
    label = "<&r&dAll&5&i&dum&r> ",
    import_timeout = 5,
    updates = {
        notify = {
            dependencies = true,
            plugins = true,
            allium = true
        },
        repo = {
            user = "hugeblank",
            branch = "master",
            name = "Allium"
        }
    }
}

Here are the descriptions for each field:

- `import_timeout`: The maximum amount of time it takes to wait for a plugin dependency to provide its module.
- `label`: The label the loader uses.
- `updates`: Various auto-update configurations. Server operators may want to change these from the default
  - `notify`: Configurations to trigger notifications when parts of Allium are ready for an update
    - `dependencies`: Notify when dependencies need updating
    - `plugins`: Notify when plugins need updating
    - `allium`: Notify when allium needs updating
  - `repo`: Repo specific information for Allium in case you want to use a fork
    - `user`: User to check updates from
    - `branch`: Branch/Tag to check updates from
    - `name`: Name of repo to check updates from
