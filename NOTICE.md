# Notice

This repository is a modified copy of
[AngelAuraMC/Amethyst-iOS](https://github.com/AngelAuraMC/Amethyst-iOS),
licensed under the GNU General Public License v3.0. Amethyst-iOS is itself
based on PojavLauncher and Boardwalk.

Blockys is not affiliated with AngelAuraMC, PojavLauncherTeam, Mojang Studios
or Microsoft. Minecraft is a trademark of Mojang Studios.

## Changes made on 2026-11-21

All changes are cosmetic branding plus the build workflow. The launcher logic,
mod support and rendering code are unchanged.

- `Natives/Info.plist`: display name `Blockys`, bundle name `Blockys`,
  bundle identifier `com.blockys.ios`, URL scheme name updated and the
  `blockys://` scheme added, version `1.0.0`, privacy usage descriptions
  renamed.
- `Natives/Assets.xcassets` and `Natives/resources`: app icons (`AppIcon-Light`,
  `AppIcon-Dark`, `AppIcon-Development`), legacy icon sizes and the navigation
  logo regenerated from the Blockys grass-block icon.
- `Natives/resources/en.lproj` and `Natives/resources/es.lproj`: visible
  strings renamed from Amethyst to Blockys.
- `Natives/LauncherPreferencesViewController.m`: the version footer now reads
  `Blockys`.
- `Natives/LauncherNewsViewController.m`: the news tab opens the Blockys
  releases page instead of the Amethyst changelog.
- `Makefile`: version string `1.0.0`.
- `.github/workflows`: the upstream workflows target Amethyst's self-hosted
  runners and were removed; `ios.yml` builds the IPA on a GitHub-hosted macOS
  runner and publishes it to Releases.
- `README.md` and this file were rewritten for the fork.

The upstream license, copyright notices and third-party components are
unchanged.
