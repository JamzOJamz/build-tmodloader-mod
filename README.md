# Build tModLoader Mod

A GitHub Action that builds a [tModLoader](https://github.com/tModLoader/tModLoader) mod and optionally uploads the `.tmod` as a workflow artifact. It can be used to build every commit automatically, for example so players can easily try development versions of your mod between Steam Workshop releases.

## Usage

```yaml
name: Build

on: [push, pull_request, workflow_dispatch]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v7
      - uses: JamzOJamz/build-tmodloader-mod@v1
```

By default, it builds the single `.csproj` in the repo root against the latest stable tModLoader release. If your mod lives in a subfolder or you want to pin a tModLoader version:

```yaml
- uses: JamzOJamz/build-tmodloader-mod@v1
  with:
    project: src/MyMod.csproj
    tml-version: v2026.08.3.0
```

## Inputs

| Input | Description | Default |
| --- | --- | --- |
| `project` | Path to the mod's `.csproj`, relative to the repo root | The single `.csproj` in the repo root |
| `tml-version` | tModLoader release tag to build against | Latest stable release |
| `dotnet-version` | .NET SDK version(s) to install, one per line | `8.0.x` |
| `configuration` | Build configuration | `Release` |
| `upload-artifact` | Upload the built `.tmod` as a workflow artifact | `true` |
| `artifact-name` | Name of the uploaded artifact | `<csproj name>-tmod` |

Requires a Linux runner. Use the default `actions/checkout` path.

## License

[MIT](LICENSE)
