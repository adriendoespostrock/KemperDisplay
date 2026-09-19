# Kemper Display

A lightweight macOS menu bar companion for the **Kemper Profiler Player**.

Kemper Display connects to the Profiler over USB MIDI, shows the current Rig information in the macOS menu bar, and serves a responsive local web interface that can be opened from a phone or tablet on the same network.

> **Unofficial community project.**  
> Kemper Display is not affiliated with, endorsed by, or supported by Kemper GmbH.

## Features

- Automatic Kemper Profiler detection over USB MIDI
- macOS menu bar app — no main application window required
- Current Rig name
- Bank and Slot display
- BPM display
- Automatic Bank/Slot synchronization
- Eight effect slots:
  - A
  - B
  - C
  - D
  - X
  - MOD
  - DLY
  - REV
- Effect on/off state
- Effect type names
- Responsive local web interface for phone/tablet
- MIDI channel selector:
  - Omni
  - MIDI channels 1–16
- Automatic reconnection when the Profiler is unplugged and reconnected
- Menu bar status showing whether the Profiler is connected

## Requirements

- macOS
- Kemper Profiler Player
- USB MIDI connection between the Mac and the Profiler
- Xcode if you want to build the project from source

## How it works

Kemper Display communicates directly with the Profiler using CoreMIDI and Kemper SysEx messages.

The application runs entirely from the macOS menu bar. It also starts a small HTTP server on port `8080`, allowing the current Rig and effects to be displayed in a browser on another device.

Typical setup:

```text
Kemper Profiler Player
        │
        │ USB MIDI
        ▼
      Mac
        │
        ├── Kemper Display menu bar app
        │
        └── Local web server :8080
                   │
                   ├── iPhone
                   └── Android / tablet
```

## Web interface

With Kemper Display running, open the local web interface from the menu bar.

To display it on a phone or tablet connected to the same local network, open:

```text
http://YOUR-MAC-IP:8080
```

For example:

```text
http://192.168.1.25:8080
```

The web interface updates automatically when the Rig or effect state changes.

## MIDI channel

The menu bar app lets you choose:

- **Omni** — listens to channel messages on all MIDI channels
- **1–16** — only listens to Control Change and Program Change messages on the selected MIDI channel

Kemper SysEx communication remains independent from this setting.

The selected MIDI channel is saved automatically.

## Building from source

1. Create or open a macOS SwiftUI app project in Xcode.
2. Add `Sources/KemperDisplayMenuBarApp.swift` to the application target.
3. Make sure there is only one `@main` entry point in the target.
4. Enable the network permissions required for the local web server, or disable App Sandbox for a personal build.
5. Build and run the project.
6. Connect the Kemper Profiler Player via USB.

For a menu-bar-only application, the code uses an accessory activation policy so the app does not need to appear in the Dock.

## Network

The local web interface listens on:

```text
TCP port 8080
```

If macOS blocks the listener while App Sandbox is enabled, allow **Incoming Connections (Server)** in the target's App Sandbox capabilities.

## Current status

The project is currently a community beta. It has primarily been developed and tested with the **Kemper Profiler Player**.

Feedback and testing on other Kemper Profiler models are welcome.

## Contributing

Bug reports, compatibility feedback, and pull requests are welcome.

When reporting a MIDI-related issue, it is useful to include:

- Kemper model
- Profiler OS version
- macOS version
- selected MIDI channel
- whether the connection is USB MIDI or another MIDI interface
- the behavior you expected
- the behavior you observed

## Credits

Developed by **Adrien Deurveilher**.

Adrien plays in the instrumental post-rock band **When Waves Collide**.

[When Waves Collide on YouTube](https://www.youtube.com/@WhenWavesCollide)

## Trademarks

Kemper, Profiler, and related product names and trademarks belong to their respective owners. Their use here is only to describe compatibility with the hardware.

## License

A license has not been selected yet.

Before accepting external contributions or encouraging redistribution of the source code, add an explicit open-source license such as MIT, Apache-2.0, GPL-3.0, or another license appropriate for the project.
