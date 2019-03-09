Everything documented here is going to be found in the [unstable-as](https://github.com/hugeblank/Allium/tree/unstable-as) branch. This page is not guaranteed to be up to date with the unstable branch, and there also is absolutely no guarantee that the functions documented here work as intended, or at all. I test them though, there shouldn't be anything mind-bogglingly obvious. Though I am only human...


# Utils
Allium now has several utilities guaranteed on installation in the `lib` directory.

- `nap`: Translates typical Lua API calls into a REST API URL. [Link](https://github.com/hugeblank/tree/master/qs-cc/src/nap.lua)
- `gget`: Command line util to install github repositories. [Link](https://github.com/hugeblank/tree/master/qs-cc/src/gget.lua)
- `semver`: Parses a valid semver version string into an object with comparison metamethods. [Link](https://github.com/hugeblank/semparse)
- `json`: Encodes/Decodes JSON to Lua tables. [Link](https://github.com/rxi/json)

# API
The API has a couple of new features based around the SemVer grind I've been on:
## `Allium`
### Functions
#### `verify`
Compare one or two SemVer strings to the Allium version

- **Parameters**
  - _string_: minimum version
  - _string_: maximum version
- **Returns**
  - _boolean_: true when the min version exists and is *lt* Allium's version and the max version exists and is *gt* Allium's version

### Other
_table_ `version`: Allium's current version, parsed as a SemVer table