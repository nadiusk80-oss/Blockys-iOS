# Blockys (iOS)

Blockys for iPhone and iPad runs Minecraft: Java Edition with Forge, Fabric,
NeoForge, Quilt and OptiFine mods. It is the iOS counterpart of Blockys Mobile
for Android, and a rebrand of
[Amethyst-iOS](https://github.com/AngelAuraMC/Amethyst-iOS) (GPL-3.0), which is
based on [PojavLauncher](https://github.com/PojavLauncherTeam/PojavLauncher_iOS)
and zhuowei's [Boardwalk](https://github.com/zhuowei/Boardwalk).

Like Blockys Mobile, it also works without a Microsoft account: create a
local account, pick a version and loader, and the game files download and
launch with it.

Blockys is not affiliated with AngelAuraMC, PojavLauncherTeam or Mojang Studios.
Minecraft is a trademark of Mojang Studios.

## Downloads

Every IPA is built by GitHub Actions on a macOS runner and published in
[Releases](https://github.com/nadiusk80-oss/Blockys-iOS/releases). The current
release is 1.0.4:

- `Blockys-iOS-<version>.ipa`: unsigned build for TrollStore, AltStore,
  SideStore or StikDebug. It includes the Java 8, 17, 21 and 25 runtimes.
- `Blockys-iOS-<version>-trollstore.tipa`: same build with the TrollStore JIT
  entitlement already applied.

`SHA256SUMS.txt` is published next to each asset.

## Requirements

- iOS 14.0 or later on an arm64 device: iPhone 6s and later, iPad (5th
  generation) and later, iPad Air 2 and later, iPad mini 4 and later, or any
  iPad Pro.
- JIT enabled. Minecraft Java needs just-in-time compilation; without it the
  game is unusably slow.
- About 2 GB free storage for the app, the Java runtimes and game files.

Tested device tiers and the JIT options are documented upstream:
[TrollStore](https://github.com/opa334/TrollStore) permanently signs the app
and enables JIT on the iOS versions it supports. On iOS 17.4 and later,
AltStore, SideStore or StikDebug enable JIT with a computer.

**Known limitation:** upstream Amethyst does not support iOS 26 or later,
because Apple removed the JIT paths the launcher relies on. iOS 14 to 18 is
the supported range.

## Installing

1. Download `Blockys-iOS-<version>.ipa` (or the `.tipa` for TrollStore).
2. Open it with TrollStore, AltStore, SideStore or StikDebug and confirm the
   install.
3. Enable JIT for Blockys before launching.
4. Open Blockys and add an account: a Microsoft account that owns Minecraft
   Java Edition, a local account (no Microsoft login needed), or demo mode.
5. Pick a Minecraft version and loader, then press play. The first launch
   downloads the game files.

## Building

The build needs macOS with Xcode, CMake, GNU make, JDK 8 and
[ldid](https://github.com/ProcursusTeam/ldid). The GitHub workflow
`.github/workflows/ios.yml` installs everything and runs:

```sh
git submodule update --init --recursive
BOOTJDK="$(/usr/libexec/java_home -v 1.8)/bin" \
  gmake -j"$(sysctl -n hw.ncpu)" package PLATFORM=2
```

The Java runtimes are downloaded from the Amethyst asset server at build time.
The resulting IPA is unsigned.

## What is different from Amethyst

See [NOTICE.md](NOTICE.md). In short: name, icon, bundle identifier
(`com.blockys.ios`), interface strings, the changelog link, the build fixes and
one behavior change: local accounts can install and play Minecraft, the same
rule as Blockys Mobile. Blockys iOS 1.0.3 added Minecraft 26.x support
(LWJGL 3.4.1 and Java 25) and 1.0.4 continues the iOS numbering; the SDL repairs
in Blockys Mobile 2.0.7 are Android-only and have no iOS counterpart.

## License

GNU General Public License v3.0, the same license as Amethyst-iOS. See
[LICENSE](LICENSE). The full corresponding source for every release is this
repository at the release tag.
