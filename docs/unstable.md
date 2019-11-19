# Unstable

Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. Note: This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...

## Persistent no longer persists

Well it's not called persistence anymore. get/setPersistence are gone and replaced with a magical table that sticks around even after startup. I've called it the cache because that's pretty much what it is.

## Plugin update micromanager

Allium now offers a micromanager that allows for hooking into the update service that also handles the updating of Allium and dependencies. Two functions are required to manage updating, a function to check whether an update is necessary, and a function to actually perform the update. Currently implemented is a basic github checker and runner, and a pastebin checker and runner. The github methods require a user name, repo name, branch name, and optional path name to be provided in the update cache. The pastebin methods only require a paste ID, and a path name to be provided in the same cache.

## Online library micromanager

Also provided is a system for you to download and locally save libraries that your plugin needs. All that's needed is a table where the keys are the libraries name, and the value is the URL to locate it at. It also manages un-needed libraries automatically if you hook into the update micromanager
