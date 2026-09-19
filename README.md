# OpenAC plugin list

The list of plugins the [OpenAC](https://github.com/eriknihlen/OpenAC) launcher shows in its
**Discover** panel. The launcher reads `plugins.json` from this repository's latest release.

## Getting a plugin listed

Open an issue here with your plugin's id, display name, author name, a one-line description and
the `owner/name` of its GitHub repository. Before asking, publish a release the launcher can
install and check the zip with `acdream-plugincheck`; the rules are in OpenAC's
[plugin development guide](https://github.com/eriknihlen/OpenAC/blob/main/docs/plugin-development.md).

A plugin does not need to be listed to be installed: **Add from URL** in the launcher takes any
public repository with a conforming release.

## What listing means

A listed plugin has passed the mechanical checks and been looked at. It has not been audited.
Plugins run with the full rights of the game client. A plugin can be blocked later, by id and
version, with a reason the launcher shows.

## Publishing the list

Edit `plugins.json`, commit, then publish it as the asset of a new release:

    gh release create list-YYYY-MM-DD plugins.json --title "Plugin list YYYY-MM-DD" --notes "..."

The list must contain at least one plugin; the launcher refuses an empty one.
