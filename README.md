# OpenAC plugin list

The list of plugins the [OpenAC](https://github.com/eriknihlen/OpenAC) launcher shows in its
**Discover** panel. The launcher reads `plugins-rust.json` from this repository's latest release.

| File | Launcher | Plugins |
|---|---|---|
| `plugins-rust.json` | [OpenAC](https://github.com/eriknihlen/OpenAC) (the Rust client) | WebAssembly plugins |
| `plugins.json` | OpenAC (C#), retired at 0.1.33 | .NET plugins; **frozen** |

The C# client is retired: `plugins.json` no longer changes, but every list release still carries it
so that the last C# launchers keep their plugin list. Its history is on the `deprecated` branch.
An entry in `plugins-rust.json` names its client with `"client": "openac-rust"` (the launcher's
name for the Rust client; it stays as it is).

## Writing a plugin

The documentation is at **[eriknihlen.github.io/OpenAC](https://eriknihlen.github.io/OpenAC/)**:
[the Rust client](https://eriknihlen.github.io/OpenAC/docs/rust-client.html) and its plugin API
versions, and the [plugin development guide](https://eriknihlen.github.io/OpenAC/docs/plugin-development.html).

## Getting a plugin listed

Open an issue here with your plugin's id, display name, author name, a one-line description and the
`owner/name` of its GitHub repository. Publish a release tagged `wasm-v<version>` (not marked latest
if the repository also has other releases), with `plugin.json`, `<id>-<version>.zip` and its
`.sha256`, made and checked with `plugincheck pack`; the rules are in the
[plugin development guide](https://eriknihlen.github.io/OpenAC/docs/plugin-development.html).
A repository publishing several plugins (a suite) tags each release `wasm-<id>-v<version>` instead
and keeps a `plugins-index.json` on a `wasm-index` release, as the guide describes; open one issue
per plugin as each is released.

A plugin does not need to be listed to be installed: **Add from URL** in the launcher takes any
public repository with a conforming release.

## What listing means

A listed plugin has passed the mechanical checks and been looked at. It has not been audited. A
WebAssembly plugin runs in a sandbox and can use only the permissions its `plugin.json` declares,
which the launcher shows before installing. If deemed necessary, a plugin can be blocked later, by
id and version (and by client), with a reason the launcher shows.
