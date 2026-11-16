# Precise Godot

GitHub Actions pipeline that builds double-precision, C#-enabled Godot 4.4+ versions from source.

I made this mainly to offload Godot's lengthy compilation process from my own PC and let GitHub Actions handle the heavy lifting.

## Features

- Double precision (`f64`)
- C# support
- Jolt Physics (built-in on Godot 4.4+)
- Windows, Linux (x86_64)
- Production build, no debug symbols
- Includes Release export template, optional Debug
- Build caching between runs
- On-demand upstream sync

## Notes

- **Godot 4.4+ recommended** — 3.x has no `precision` scons option. For 4.0–4.3 builds, add the [Godot Jolt GDExtension](https://github.com/godot-jolt/godot-jolt) to your project's `addons/` folder separately.
- **Jolt Physics** is built directly into Godot 4.4+ by default.
- The .NET SDK must match the branch (4.7 → `8.0.x`).
- Double builds say so in the filename: `godot.windows.editor.x86_64.double.mono.exe`. Glob for it, don't hardcode.
- Optional Windows deps (D3D12, AccessKit, ANGLE) are skipped quietly if their install fails.
- Linux uses `lto=none`; `production=yes` would otherwise enable full LTO under GCC.
- The sync workflow pushes with the `SYNC_TOKEN` secret — a **fine-grained PAT** with contents write access. The default `GITHUB_TOKEN` didn't work here, and without the secret the job fails at checkout. Building doesn't need it.

## Usage

1. Run **Sync with Official Godot Repo** → pick upstream and target branch.
2. Run **Build Custom Godot** → pick branch and platform.
3. Download `godot-<branch>-<platform>` from the artifacts.

Artifacts hold the binaries, `GodotSharp/`, and the `.nupkg` files. For C# projects use those nupkgs — the official ones are single precision. Addons built for single precision won't load either.

Cold builds take significantly longer, cached repeats are much faster.

## Links

- [Godot Engine](https://github.com/godotengine/godot)
- [Godot Documentation](https://docs.godotengine.org/)