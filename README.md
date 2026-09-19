# Kemper Display

A lightweight macOS menu bar companion for the **Kemper Profiler Player**.

Kemper Display connects to the Profiler over USB MIDI, shows the current Rig information in the macOS menu bar, and serves a responsive local web interface that can be opened from a phone or tablet on the same network.

> **Unofficial community project.**  
> Kemper Display is not affiliated with, endorsed by, or supported by Kemper GmbH.

## Download

Kemper Display is distributed as a ready-to-use macOS application.

Download the latest version from the **Releases** section of this repository.

The source code is not published in this repository.

## Installation

1. Download the latest Kemper Display release.
2. Unzip the archive if necessary.
3. Move **Kemper Display.app** to your **Applications** folder.
4. Connect your Kemper Profiler Player to your Mac via USB.
5. Launch **Kemper Display**.

That's it — no additional software or setup is required.

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
- Automatic detection when the Profiler is disconnected or reconnected
- Menu bar status showing whether the Profiler is connected

## Requirements

- A Mac running macOS
- Kemper Profiler Player
- USB connection between the Mac and the Profiler

## How it works

Kemper Display communicates directly with the Profiler over USB MIDI using CoreMIDI and Kemper SysEx messages.

The application runs entirely from the macOS menu bar. It also starts a small local web server on port `8080`, allowing the current Rig and effects to be displayed in a browser on another device.

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

With Kemper Display running, choose **Open Web Interface** from the menu bar.

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

## Network

The local web interface listens on:

```text
TCP port 8080
```

The phone or tablet used for the web display must be able to reach the Mac over the local network.

## Current status

The project is currently a community beta. It has primarily been developed and tested with the **Kemper Profiler Player**.

Feedback and testing on other Kemper Profiler models are welcome.

## Feedback and bug reports

Please use GitHub Issues for bug reports and compatibility feedback.

For MIDI-related issues, it is useful to include:

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

## Source code

The source code for Kemper Display is not distributed through this repository. This repository is used for application releases, documentation, screenshots, and issue tracking.
