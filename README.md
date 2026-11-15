# apple-tv-open-control

Open IP control drivers for Apple TV on Crestron 4-Series, Extron IPCP Pro xi and Q-SYS, built on pyatv's protocol work.

[![Release](https://img.shields.io/github/v/release/rob-paprocki/apple-tv-open-control)](https://github.com/rob-paprocki/apple-tv-open-control/releases)
[![CI](https://github.com/rob-paprocki/apple-tv-open-control/actions/workflows/ci.yml/badge.svg)](https://github.com/rob-paprocki/apple-tv-open-control/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/github/license/rob-paprocki/apple-tv-open-control)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/rob-paprocki/apple-tv-open-control)](https://github.com/rob-paprocki/apple-tv-open-control/commits/main)

> **Status: design stage.** There is no driver to install yet. The first release (0.1.0) sets up the repository, and the drivers arrive in later versions.

The goal is one Apple TV protocol implementation, written three times (Python, C# and Lua) against the same test vectors, so a room controller can drive an Apple TV with no license key, no phone-home and no vendor pairing tool. The protocol work comes from [pyatv](https://github.com/postlund/pyatv) 0.18.0 (MIT).

## What it aims to do

- Send every Companion command and read every Companion feedback source that pyatv 0.18.0 implements, up to what each platform can show.
- Show now-playing state (play state, title, artist, album, app, position, shuffle, repeat, volume) through MRP inside the AirPlay 2 tunnel, with absolute seek.
- Control playback that a phone app AirPlays to the Apple TV, and pick which AirPlay speakers the Apple TV plays through.
- Pair on site from the PIN on the TV, with a PC tool as the fallback.
- Stay connected without polling or retrying an Apple TV that is asleep.

**Does not:** support tvOS older than 15, stream audio or cast URLs to the Apple TV, take Siri voice input, run as a hosted service, or claim Crestron certification.

## Planned deliverables

| Platform | Deliverable | Status |
|----------|-------------|--------|
| Crestron 4-Series (SIMPL) | SIMPL# library (`.clz`) and a SIMPL+ wrapper | Not started |
| Crestron Home OS | Driver package (`.pkg`) | Not started |
| Extron IPCP Pro xi | Global Scripter module (`.py`) and a Global Configurator driver (`.pkp`) | Not started |
| Q-SYS | Plugin (`.qplug`) | Not started |
| Any PC | Python pairing tool that produces the credentials | Not started |

Crestron 3-Series and non-xi Extron processors are out of scope for now.

## Requirements

| Item | Supported |
|------|-----------|
| Apple TV | HD or 4K on tvOS 15 or later |
| Extron | IPCP Pro xi family, ControlScript firmware 1.0.5 and up |
| Crestron | 4-Series processors |
| Q-SYS | Cores that run Lua plugins |

## Install

Nothing to install yet. To follow along or run the repository's own checks:

```bash
git clone https://github.com/rob-paprocki/apple-tv-open-control.git
cd apple-tv-open-control
python3 -m unittest discover -s tests
```

## Quick start

The planned setup, once drivers exist:

1. Pair with the Apple TV, either from the PIN on the TV or with the PC tool.
2. Load the driver for your platform and give it the Apple TV's address and credentials.
3. Wire the transport, power and feedback signals into your program.

## Help and contributing

Questions, bug reports and ideas go in [Issues](https://github.com/rob-paprocki/apple-tv-open-control/issues). Releases come from a separate development repository, so a pull request here is not merged directly. A good one gets copied over by hand and ships with the next release.

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE) (c) 2026 Rob Paprocki. Apple, Crestron, Extron and Q-SYS are trademarks of their owners, and this project is not affiliated with any of them.
