# OpenAC plugin list

The lists of plugins the OpenAC launchers show in their **Discover** panel. Each launcher reads its
own file from this repository's latest release:

| File | Launcher | Plugins |
|---|---|---|
| `plugins.json` | [OpenAC](https://github.com/eriknihlen/OpenAC) (C#) | .NET plugins |
| `plugins-rust.json` | [OpenAC-rust](https://github.com/eriknihlen/openac-rust) | WebAssembly plugins |

Every list release carries both files. An entry in `plugins-rust.json` names its client with
`"client": "openac-rust"`; a plugin that exists for both clients keeps the same id in both lists.

## Getting a plugin listed

Open an issue here with your plugin's id, display name, author name, a one-line description, the
`owner/name` of its GitHub repository, and which client it is for.

- **OpenAC (C#):** publish a release the launcher can install and check the zip with
  `acdream-plugincheck`; the rules are in OpenAC's
  [plugin development guide](https://github.com/eriknihlen/OpenAC/blob/main/docs/plugin-development.md).
- **OpenAC-rust (WebAssembly):** publish a release tagged `wasm-v<version>` (not marked latest, so a
  C# release can stay the repository's latest), with `plugin.json`, `<id>-<version>.zip` and its
  `.sha256`, made and checked with `plugincheck pack`; the rules are in OpenAC-rust's
  [plugin development guide](https://github.com/eriknihlen/openac-rust/blob/main/docs/plugin-development.md).
  A repository that ships both clients should publish the C# and WebAssembly builds of a version
  together.

A plugin does not need to be listed to be installed: **Add from URL** in either launcher takes any
public repository with a conforming release.

## What listing means

A listed plugin has passed the mechanical checks and been looked at. It has not been audited.
A .NET plugin runs with the full rights of the game client. A WebAssembly plugin runs in a sandbox
and can use only the permissions its `plugin.json` declares, which the launcher shows before
installing. If deemed necessary, a plugin can be blocked later, by id and version (and, in
`plugins-rust.json`, by client), with a reason the launcher shows.
