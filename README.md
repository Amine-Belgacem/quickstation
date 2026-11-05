# QuickStation

A compact Windows internet radio player with favorites, station discovery, and playlist import/export. Built with C++20, Win32, BASS, and BASSHLS.

## Features

- Browse the Radio Browser directory by country, genre, or station name.
- Save favorites or add a stream URL directly.
- Play supported audio and HLS streams with station-provided song metadata.
- Import and export JSON, M3U, and M3U8 playlists.
- Control playback from the keyboard and retain local preferences between runs.

## Build and run

Requires Windows 10 version 1709 or later / Windows 11 x64, Visual Studio 2022 with **Desktop development with C++**, the Windows SDK, and CMake.

```powershell
powershell -File tools\build.ps1
```

The script builds, tests, and packages the application under `dist`. Extract the whole package and open `QuickStation.exe`; keep `QuickStationAudio.exe`, `bass.dll`, and `basshls.dll` beside it.

## Use

Click a station to listen. Open **Stations > Browse stations** to discover more, or **Stations > Add by URL** for a known stream. Manage saved stations and favorites through their context menus.

Station data lives in `%LOCALAPPDATA%\SmallRadio\stations.json`; the legacy profile name is retained for compatibility. Playback and discovery need internet access. Availability and metadata depend on the broadcaster.

## Documentation

[Detailed reference](docs/reference.md) · [Validation](VALIDATION.md) · [Third-party notices](THIRD_PARTY_NOTICES.md)

BASS/BASSHLS licensing depends on usage; review the notices before commercial distribution.
