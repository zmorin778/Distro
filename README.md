# Song Sorter

A desktop app for ranking your music through head-to-head comparisons, instead
of guessing where a song belongs in a flat list.

This repo hosts **downloads and release notes only**. There's no source code here.

## Download

Grab the latest build from [Releases](../../releases/latest):
`SongSorter.zip` for Windows, `SongSorter.tar.gz` for Linux.

## Requirements

- Windows 10 or 11, 64-bit, **or** a 64-bit desktop Linux with GTK 3.
- Nothing else. Java is bundled inside the app.
- The two downloads are separate: the Windows zip won't run on Linux, and the
  other way round.

## Running it on Windows

1. Right-click the zip → **Extract All**, and put the folder anywhere — Desktop,
   a USB stick, wherever.
2. Open the `SongSorter` folder and double-click `SongSorter.exe`.
3. Windows will likely show a **“Windows protected your PC”** SmartScreen
   warning. That's expected: the app isn't code-signed (certificates cost money,
   and this is a free personal project). Click **More info → Run anyway**.

No installer, no admin rights, and nothing is written outside that folder.

## Running it on Linux

```
tar xzf SongSorter.tar.gz
./SongSorter/bin/SongSorter
```

Put the folder anywhere; nothing is installed.

- **Unpack with `tar`**, not a graphical tool that re-zips the archive. If the
  launcher says *permission denied*, that's what happened:
  `chmod +x SongSorter/bin/SongSorter` fixes it.
- **The app needs GTK 3**, which nearly every desktop Linux has. If it exits
  complaining about a missing library, install it — on Debian/Ubuntu,
  `sudo apt install libgtk-3-0 libxtst6`.
- **Signing in:** the app tries to open your browser and always shows the sign-in
  link in a window you can copy it from. If no browser opens, paste the link in
  yourself.

## Your data

Everything you do (rankings, groups, Boop and so on) is saved in a `data` folder
inside `SongSorter`, next to `SongSorter.exe` on Windows. It's the same place
whichever directory you start the app from.

**From 4.8 on, Windows copies update themselves.** A few seconds after it
opens, Song Sorter says when a new version is out. **Update and Restart**
downloads it, and the app closes and opens again on it. **Later** leaves an
**Update** button on the bottom bar. Your `data` folder stays as it is, and a
copy of it from before each update is kept in `backups`.

To upgrade by hand on Windows (and from any version before 4.8):

1. **Close Song Sorter.** Windows can't overwrite a running program, and the
   upgrade stops partway if you skip this.
2. Download the new release and **Extract All**. You get a folder called
   `SongSorter`.
3. Drag it into the folder that holds your current `SongSorter`. Say yes to
   merging, then **Replace the files in the destination**.

That's it. `data` isn't part of the download, so nothing you've ranked is
touched, and shortcuts and taskbar pins still work.

If a version misbehaves after upgrading that way, extract it into a fresh folder
instead and copy your old `data` folder across.

## Connecting a music service

Song Sorter ranks songs without one, but importing and publishing playlists needs
Spotify or YouTube Music. **One collection uses one service**, so a YouTube
collection lives in its own `data` folder. The **Account** tab is where you sign
in, and if credentials are missing it shows the exact folder to put them in.

### Spotify

The public download doesn't include Spotify keys. Either:

- ask for a copy that's set up for you (your Spotify account also has to be
  added on the developer side while the app is in early access), or
- create your own app at the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
  and follow `spotify_credentials.properties.example` in the `data` folder.

You always log in with **your own** Spotify account. The login is saved on your
machine and is never part of a download.

**Playing songs.** The ▶ buttons change the track on whatever device Spotify is
already playing on — your phone, your desktop app, wherever. They need:

- **Spotify Premium** on your account; Spotify doesn't allow playback control on
  free accounts.
- **Something already playing.** Start any track first. If nothing is playing,
  the app says so and lists the devices it can see.

If Spotify won't start a song directly, the app plays it through a private
playlist called **Song Sorter Now Playing**, and tells you once when it makes it.

### YouTube Music

You need a free Google Cloud project with **YouTube Data API v3** enabled,
yourself added as a test user on the consent screen, and an OAuth client of type
**Desktop app**. Save the JSON file Google gives you as
`data/youtube_credentials.json` and restart. `youtube_credentials.properties.example`
in the `data` folder walks through the same steps.

- Google expires the sign-in after **seven days** while the consent screen is in
  Testing. The app says so and offers to sign in again.
- There's a **daily budget** of 10,000 units. Reading is nearly free; adding or
  moving one song costs 50. The Account tab shows what's left, and an update that
  wouldn't fit is refused before anything changes.
- Playing songs from inside the app is Spotify-only for now.

## Found a bug, or have feedback?

Open an issue on this repo's [Issues](../../issues) tab.

## What's new

See [Releases](../../releases) for version history.
