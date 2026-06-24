# 🧟 NZ:P Switch Emulator Edition — Citron CI

[![Build Citron (Nightly)](https://github.com/CollectingW/CI/actions/workflows/build_nightly.yml/badge.svg)](https://github.com/CollectingW/CI/actions/workflows/build_nightly.yml)

## What is this?

This is the build/CI repository for **[NZ:P Switch Emulator Edition](https://github.com/CollectingW/NZ-P-Switch-Emulator-Edition)** — a fork of the official [Citron-CI](https://github.com/citron-neo/CI), repointed to build my customized fork of the Citron Switch emulator at **[CollectingW/emulator](https://github.com/CollectingW/emulator)** instead of upstream Citron.

## Why does it exist?

NZ:P Switch Emulator Edition pairs a heavily-modified Nintendo Switch build of **Nazi Zombies: Portable** with a **matching fork of the Citron emulator**, so the game and the emulator are tuned to run together. The emulator fork adds, among other things:

* **Nintendo Switch 2 Joy-Con 2** controller support (detection, naming, pairing)
* **ETC2 texture format** support (for NZ:P's compressed textures)
* Additive **GL/GR back-button** remapping in the input UI
* UI tweaks (dark theme, custom background, icon/poster handling)

Upstream's CI builds upstream Citron, which wouldn't include any of those changes — so this fork's workflows clone and build **`CollectingW/emulator`** and publish the resulting AppImages / packages, giving anyone the customized emulator that goes with the game.

## What it builds

The nightly workflow builds **Linux** (x86_64, x86_64_v3, aarch64), **Windows**, **macOS**, and **Android** from the emulator fork, daily at 12:00 UTC (and on manual dispatch). The **Linux AppImage** is the primary target for this edition.

* [Latest emulator commits](https://github.com/CollectingW/emulator/commits/main)
* Nightly releases are published on this repo's [Releases](https://github.com/CollectingW/CI/releases) page.

---

# READ THIS IF YOU HAVE ISSUES

If you are on Wayland (especially GNOME Wayland) and get freezes or crashes, you are likely affected by an issue that affects all Qt6 apps. To fix it, set the env variable:

```
QT_QPA_PLATFORM=xcb
```

---

AppImages are made using [sharun](https://github.com/VHSgunzo/sharun), which makes it easy to turn any binary into a portable package without containers. **They bundle everything and should work on any Linux distro, even musl-based ones.** They work without fuse2 (using fuse3, or no fuse at all) thanks to the [uruntime](https://github.com/VHSgunzo/uruntime).

If AppImages fail with appimagelauncher, try [AM](https://github.com/ivan-hc/AM), [dbin](https://github.com/xplshn/dbin), or [soar](https://github.com/pkgforge/soar).

---

## Credits

This is an unofficial personal fork. All credit for the emulator and its CI goes to the **Citron team** and to **[pkgforge](https://github.com/pkgforge-dev/Citron-AppImage)**, whose AppImage work this CI derives from. This fork only repoints the build at my Switch-focused emulator fork; the heavy lifting is theirs.
