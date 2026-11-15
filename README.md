
# Precise Godot

A GitHub Actions build pipeline for my double-precision C# Godot builds straight from source.

I made this mainly to offload Godot's lengthy compilation process from my own PC and let GitHub Actions handle the heavy lifting.

## Features

- Double precision (`f64`)
- C# support
- Jolt Physics
- Windows and Linux builds
- On-demand upstream syncing
- Includes Release and optional Debug export templates

## Usage

1. Run **Sync with Official Godot Repo**.
2. Select the upstream and target branches.
3. Run **Build Custom Godot**.
4. Select your custom branch and target platform.
5. Download the build from GitHub Actions artifacts.

---

Godot source branches are created on demand. No local compilation required.

## Links

- [Godot Engine](https://github.com/godotengine/godot)
- [Godot Documentation](https://docs.godotengine.org/)