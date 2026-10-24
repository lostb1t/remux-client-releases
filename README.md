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

## Web, as a Docker image

The web app is also a container image, for `linux/amd64` and `linux/arm64`. It is public: no login
is needed to pull it.

- Image: `ghcr.io/lostb1t/remux-client`
- Package page: <https://github.com/users/lostb1t/packages/container/package/remux-client>
- Tags: `nightly` is the newest build; `sha-<commit>` is one build, for pinning a version (the
  commit is in the name of the files on [Releases](../../releases) too).

```sh
docker run -d --name remux-client -p 8080:80 ghcr.io/lostb1t/remux-client:nightly
```

or with Compose:

```yaml
services:
  remux-client:
    image: ghcr.io/lostb1t/remux-client:nightly
    ports:
      - "8080:80"
    restart: unless-stopped
```

The app is then at <http://localhost:8080>; it asks for the address of your server when you sign in.
The image only serves the app (a small static web server): an address such as `/media/Movie/…` is
handled by the app itself, so any address should give the page.

To update, pull the tag again and restart the container
(`docker pull ghcr.io/lostb1t/remux-client:nightly`).

## Web, without Docker

Every build also has `remux-web-<commit>.zip` on [Releases](../../releases): the same files, to unpack
in the folder of a web server. The server has to answer any address that is no file with
`index.html`, as the app has its own router, and the app has to be served from the root of its
address (not from a folder such as `/app/`).

