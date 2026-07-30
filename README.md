# 🧟 NZ:P Switch Emulator / Nextendo Network Citron Neo Fork

[![Build Citron (Nightly)](https://github.com/CollectingW/CI/actions/workflows/build_nightly.yml/badge.svg)](https://github.com/CollectingW/CI/actions/workflows/build_nightly.yml)

## What is this?

This is the build/CI repository for **[NZ:P Switch Emulator Edition](https://github.com/CollectingW/NZ-P-Switch-Emulator-Edition)** — a fork of the official [Citron-CI](https://github.com/citron-neo/CI), repointed to build my customized fork of the Citron Switch emulator at **[CollectingW/emulator](https://github.com/CollectingW/emulator)** instead of upstream Citron.

## Why does it exist?

NZ:P Switch Emulator Edition pairs a heavily-modified Nintendo Switch build of **Nazi Zombies: Portable** with a **matching fork of the Citron emulator**, so the game and the emulator are tuned to run together. The emulator fork adds, among other things:

* **Nintendo Switch 2 Joy-Con 2** controller support (detection, naming, pairing)
* **ETC2 texture format** support (for NZ:P's compressed textures)
* Additive **GL/GR back-button** remapping in the input UI
* Multiplayer co-op functionality VIA LDN w/ Yuzu Online servers to connect to friends & play co-op (REQUIRES GAME TO BE TURNED OFF & JOIN A LOBBY FIRST BEFORE RE-OPENING THE GAME TO FULLY INITIALIZE THE LDN CONNECTION)
* **Nextendo Network online play** — sign in with a Nextendo Network account and play supported retail titles online, with no hosts-file edits, external DNS, or manual SSL bypass. Browser-based sign-in (the emulator never handles your password), in-app friends list, presence, and play-time sync. **Work in progress — expect bugs.**

Upstream's CI builds upstream Citron, which wouldn't include any of's workflows clone and build **`CollectingW/emulator`** and publish
the resulting AppImages / packages, giving anyone the customized eme.

## What it builds

The nightly workflow builds **Linux** (x86_64, x86_64_v3, aarch64),**Android** from the emulator fork, daily at 12:00 UTC (and on manual
dispatch). The **Linux AppImage** is the primary target for this ed

* [Latest emulator commits](https://github.com/CollectingW/emulator
* Nightly releases are published on this repo's [Releases](https://eases) page.

---                                                                                                                                                                  # READ THIS IF YOU HAVE ISSUESIf you are on Wayland (especially GNOME Wayland) and get freezes orcted by an issue that affects all Qt6 apps. To fix it, set the envvariable:                                                                                                                                                            
QT_QPA_PLATFORM=xcb

### Reporting a bug                                                                                                                                                  
Please report **emulator or online-play problems** on the [emulator repo's issues](https://github.com/CollectingW/emulator/issues), not here — this repo only builds it. Use this repo's issues only for CI/packaging failures.

Whatever you report, include:

* your `citron_log.txt` (Linux: `~/.local/share/citron/log/citron_log.txt`)
* the exact error code the game showed, if any (e.g. `2306-0802`)
* the game, its version, and what you were doing when it broke

For online-play issues, set the log filter to `*:Info Service:Debug:Debug` before reproducing — the default filter hides everythinguseful. A log is the difference between a fixable report and a guess.

> **Never** post your Network ID (PID), and never share `nextendo_account.txt` — it holds your session token. Logs are safe to share; they don't contain either.

---

AppImages are made using [sharun](https://github.com/VHSgunzo/sharurn any binary into a portable package without containers. **Theybundle everything and should work on any Linux distro, even musl-ba fuse2 (using fuse3, or no fuse at all) thanks to the[uruntime](https://github.com/VHSgunzo/uruntime).

If AppImages fail with appimagelauncher, try [AM](https://github.com/ivan-hc/AM), [dbin](https://github.com/xplshn/dbin), or [soar](https://github.com/pkgforge/soar).

---
## Credits

This is an unofficial personal fork. All credit for the emulator and its CI goes to the **Citron team** and to **[pkgforge](https://github.com/pkgforge-dev/Citron-AppImage)**, whose AppImage work this CI derives from. This fork only repoints the build at my Switch-focused emulator fork; the heavy lifting is theirs.
