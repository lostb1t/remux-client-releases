# Remux client — builds

Builds of the Remux client for Android (phone and TV), macOS, Windows and Linux. Every build is a
pre-release under [Releases](../../releases); the newest is on top. The files say the platform and
the commit they were made from: `remux-android-<commit>.apk`, `remux-macos-<commit>.dmg`,
`remux-windows-<commit>.exe`, `remux-linux-<commit>.AppImage` (and `.deb`).

## Android, and keeping it up to date

Use [Obtainium](https://github.com/ImranR98/Obtainium), which installs the app and updates it as
new builds come out:

1. Install Obtainium.
2. Add an app, with this address: `https://github.com/lostb1t/remux-client-releases`
3. Turn on **Include prereleases** (every build is one), and add the filter `remux-android-.*\.apk`
   for the APK if it asks for one.

All builds are signed with the same key, so they install over each other.

These are test builds of an app that is being made: expect rough edges.
