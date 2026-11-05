# QuickStation

QuickStation keeps internet radio within reach in a compact Windows desktop player. Save the stations you actually listen to, browse for new ones by country or genre, or add a stream URL directly. Favorites are the default view, so returning to a station does not require another directory search.

It combines station discovery, supported live audio and HLS playback, broadcaster-provided song titles, and playlist import/export in one native interface. Automatic reconnection handles recoverable playback failures, while local settings retain your station collection between sessions. This is useful for everyday listening and maintaining your own station list; it plays live broadcasts rather than recording or time-shifting them.

Built with C++20, Win32, BASS, and BASSHLS.

## Features

- Browse the Radio Browser directory by country, genre, or station name.
- Save favorites or add a stream URL directly.
- Play supported audio and HLS streams with station-provided song metadata.
- Import and export JSON, M3U, and M3U8 playlists.
- Control playback from the keyboard and retain local preferences between runs.

## Run

Extract the complete release ZIP and open `QuickStation.exe`. Keep `QuickStationAudio.exe`, `bass.dll`, and `basshls.dll` beside it. Requires Windows 10 version 1709 or later / Windows 11, x64. No installer or administrator rights are required.

1. Click a favorite to listen. Use Play/Stop, Mute, and Volume to control playback.
2. Choose **Stations → Browse stations** to search by country, genre, or name, or **Add by URL** for a stream you already know.
3. Use checkboxes in **All stations** to manage favorites. Right-click a station to edit, reorder, or remove it.
4. Import or export JSON, M3U, and M3U8 playlists. JSON retains all station details; imports merge by stream URL without replacing existing entries.

Four SomaFM channels are included as editable starter favorites. Station availability and song metadata depend on the broadcaster. Playback reconnects after recoverable failures; Stop disconnects the live stream.

Shortcuts: **Ctrl+F** browse, **Ctrl+N** add, **Ctrl+M** mute, **Ctrl+O** import, **Ctrl+E** export, **Ctrl+Space** play/stop, **F1** help. **Options → Double-click to play** changes the default click behavior.

## Local data

Stations and preferences are stored in `%LOCALAPPDATA%\SmallRadio\stations.json`, with a backup in `stations.json.bak`. The folder name preserves compatibility with earlier releases. Window settings and cached logos are stored alongside it.

To use a portable or separate profile:

```powershell
.\QuickStation.exe --data-dir "D:\QuickStationData"
```

Only one process can use a data folder at a time. If station browsing is unavailable, saved stations and manual URLs still work; the last matching search can be reused for up to seven days.

## Build and test

Requires Visual Studio 2022 with **Desktop development with C++**, the Windows SDK, and bundled CMake. Dependencies are vendored.

```powershell
powershell -ExecutionPolicy Bypass -File tools\build.ps1
```

The script builds x64 Release, runs tests, and creates `dist/QuickStation-<version>` and `dist/QuickStation-windows-x64.zip`.

- `-Debug`: build a debug configuration.
- `-SkipPackage`: build and test without packaging.
- `-Tests native_ui`: select a CTest expression when using `-SkipPackage`.
- `-BuildDirectory <folder>`: choose a separate build directory.

See [VALIDATION.md](VALIDATION.md) for test results and compatibility checks.

## Format support and licensing

BASS supports common MP3, Ogg and WAV streams, with AAC through Windows Media Foundation codecs. BASSHLS adds HLS. Other formats may require additional codecs/plugins. Station metadata is optional and varies by protocol; not all HLS timed metadata is exposed by this version.

BASS/BASSHLS are third-party binary libraries, free for qualifying non-commercial use. Commercial use requires the appropriate Un4seen license. See `THIRD_PARTY_NOTICES.md` and the bundled license documentation before commercial distribution.
