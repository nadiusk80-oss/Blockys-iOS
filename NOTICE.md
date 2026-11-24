# Notice

This repository is a modified copy of
[AngelAuraMC/Amethyst-iOS](https://github.com/AngelAuraMC/Amethyst-iOS),
licensed under the GNU General Public License v3.0. Amethyst-iOS is itself
based on PojavLauncher and Boardwalk.

Blockys is not affiliated with AngelAuraMC, PojavLauncherTeam, Mojang Studios
or Microsoft. Minecraft is a trademark of Mojang Studios.

## Changes made on 2026-11-21

All changes are cosmetic branding, one behavior change so local accounts can
install Minecraft (the same rule as Blockys Mobile 2.0.4), build fixes for the
current iOS SDKs and the build workflow. The rendering, mod loader and game
launch code are unchanged.

- `Natives/Info.plist`: display name `Blockys`, bundle name `Blockys`,
  bundle identifier `com.blockys.ios`, URL scheme name updated and the
  `blockys://` scheme added, version `1.0.2`, privacy usage descriptions
  renamed.
- `Natives/MinecraftResourceDownloadTask.m`: the download access check no
  longer rejects local (offline) accounts; it only requires an account to be
  selected. Local accounts can create profiles, download versions and play,
  matching Blockys Mobile 2.0.4 for Android. Demo mode restrictions are
  unchanged.
- `Natives/JavaLauncher.m`: added the Mach headers so the launcher compiles
  with the iOS 18 SDK (Xcode 16), where `task_set_exception_ports` is no
  longer declared through transitive includes. No behavior change.
- `Natives/Assets.xcassets` and `Natives/resources`: app icons (`AppIcon-Light`,
  `AppIcon-Dark`, `AppIcon-Development`), legacy icon sizes and the navigation
  logo regenerated from the Blockys grass-block icon.
- `Natives/resources/en.lproj` and `Natives/resources/es.lproj`: visible
  strings renamed from Amethyst to Blockys.
- `Natives/LauncherPreferencesViewController.m`: the version footer now reads
  `Blockys`.
- `Natives/LauncherNewsViewController.m`: the news tab opens the Blockys
  releases page instead of the Amethyst changelog.
- `Makefile`: version string `1.0.2`.
- `.github/workflows`: the upstream workflows target Amethyst's self-hosted
  runners and were removed; `ios.yml` builds the IPA on a GitHub-hosted macOS
  runner and publishes it to Releases.
- `README.md` and this file were rewritten for the fork.

The upstream license, copyright notices and third-party components are
unchanged.

## Changes made on 2026-11-23 and 2026-11-24

Blockys iOS 1.0.3 added Minecraft 26.x (Java 25) launch support, and Blockys iOS
2.0.7 aligns the version number with Blockys Mobile 2.0.7.

- `Natives/JavaLauncher.m`: picks `lwjgl-3.4.1` from the launch target's
  `lwjglVersion` (falling back to the Minecraft version id), so 26.x runs with
  LWJGL 3.4.1 while older versions keep 3.3.3, and installs the Java 25 runtime
  when the version declares it. The Mach exception headers are included
  explicitly so the file builds with the current iOS SDK.
- `Natives/Info.plist`, `Natives/PLPreferences.m`, `Natives/LauncherPreferences.m`,
  `Natives/MinecraftResourceUtils.m`, `Natives/TrackedTextField.m`,
  `Natives/input_bridge_v3.m` and `Natives/resources/en.lproj/Localizable.strings`:
  the 26.x updates and line-ending normalization; content changes are the version
  strings and interface labels only.
- `.github/workflows/ios.yml`: downloads the LWJGL 3.4.1 jars and dylibs and pins
  the MobileGlues submodule to the upstream revision these builds use.
- `Makefile`, `Natives/Info.plist` and the workflow asset names: version `2.0.7`,
  build `20000007`. The SDL repairs in Blockys Mobile 2.0.7 target Android's SDL
  layer and do not apply here, because Blockys iOS does not include SDL.
