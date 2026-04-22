# Munadi

## Simple Athan App

Munadi is a lightweight, privacy-focused prayer time application for Linux and Android. It provides accurate prayer times with customizable athan (call to prayer) options, dual calendar support (Hijri/Gregorian), and a clean modern interface.

---

## Screenshots

### Version 26.04

<div style="overflow-x: auto; white-space: nowrap;">

| ![Main Page - Fajr](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/01_main_page_fajr.png) | ![Main Page - Dhuhr](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/02_main_page_dhuhr.png) | ![Main Page - Asr](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/03_main_page_asr.png) | ![Main Page - Maghrib](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/04_main_page_maghrib.png) | ![Main Page - Isha](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/05_main_page_isha.png) |
|:--:|:--:|:--:|:--:|:--:|
| Fajr | Dhuhr | Asr | Maghrib | Isha |

| ![Material Light Theme](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/06_main_page_material_light.png) | ![Material Dark Theme](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/07_main_page_material_dark.png) | ![Location Search](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2604/08_location_search.png) | ![Settings Page 1](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2511/06_settings_page.png) | ![Settings Page 2](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2511/07_settings_page.png) | ![Settings Page 3](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2511/08_settings_page.png) |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Material Light | Material Dark | Location Search | Prayer Times Settings | General Settings | Appearance Settings |

| ![Tray Menu](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2511/10_tray_menu.png) | ![Tray Tooltip](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2511/11_tray_menu.png) |
|:--:|:--:|
| Tray Menu | Tooltip |

</div>

---

> [!NOTE]
> This repository holds only the flathub manifest and flatpak related contents. For full project details, go to [project home](https://gitlab.com/munadi/munadi).

---

## Status (Flatpak)

[![Build pipeline](https://github.com/flathub-infra/vorarbeiter/actions/workflows/build.yml/badge.svg)](https://github.com/flathub-infra/vorarbeiter/actions/workflows/build.yml)

Supported Architectures:
  - x86_64
  - aarch64

---

## Features

- Prayer times for cities worldwide with multiple calculation methods
- Hijri and Gregorian calendar display
- Customizable athan files and individual prayer volume control
- System tray integration with window show/hide functionality
- Time-left countdown to next prayer
- Time-of-day themed wallpapers
- Dark and light theme support
- RTL language support (including Arabic)

---

## Installing

### Flatpak
<div align="center">
  <a href='https://flathub.org/apps/details/org.munadi.Munadi'>
    <img height='128' alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-en.png'/>
  </a>
</div>

### Primary Release

**Munadi Self-Extracting Installer**

[![Latest Release](https://gitlab.com/munadi/munadi/-/badges/release.svg)](https://gitlab.com/munadi/munadi/-/releases)

No dependencies required - just download & install:

```bash
# Replace VER with the file's version, e.g. Munadi-26.04.run
$ sh Munadi-<VER>.run -q
```

Alternatively:

```bash
$ sh ./Munadi-<VER>.run
```

and follow instructions.

---

## Building from Source

Clone the repo:

```bash
git clone --recursive --depth 1 https://github.com/flathub/org.munadi.Munadi.git ./munadi_flathub && cd ./munadi_flathub
```

The recommended method is to use `org.flatpak.Builder`:
```bash
flatpak install -y flathub org.flatpak.Builder

# Add the flathub repo user-wide
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo

# Then build the manifest
flatpak run --command=flathub-build org.flatpak.Builder --install org.munadi.Munadi.yml

# Run the app (provided no previous installation of flatpak munadi is present)
flatpak run org.munadi.Munadi
```
---

## Versioning

Version format follows [upstream convention](https://gitlab.com/munadi/munadi/-/blob/master/README.md#versioning). Follow-up published changes on this repository add revision number to upstream version: `<upstream>-<revision>` (e.g. `22.04-1` after `22.04` while the project is at `22.04`).

---

## Bug Reports

First of all, see if the issue you're facing already exists on the issue board. If not, follow these workflow before reporting bugs:

1. Run `flatpak update --appstream` and `flatpak update -y`
2. Remove old configs and caches:
```bash
mv ~/.var/app/org.munadi.Munadi{,.bak}
```
3. Run from terminal:
```bash
flatpak run --command=munadi --env=QT_DEBUG_PLUGINS=1 org.munadi.Munadi > munadi-log.txt 2>&1
```
and try reproducing the issues.

If issues persist, [open an issue on project home](https://gitlab.com/munadi/munadi/-/issues) with `munadi.log`. Explain as detail as possible with your current app version and relevant details.

---

## Contributing

- Validate your manifest:
  ```bash
  flatpak run --command=flatpak-builder-lint org.flatpak.Builder manifest /path/to/your/manifest
  ```
> [!NOTE]
> Make sure your manifest uses the [latest tagged commit of the project](https://gitlab.com/munadi/munadi/-/tags) as the source. Do not use other commits as those are not guaranteed to be stable.
- Then test build and install [following the recommended workflow](#building-from-source). Replace with your manifest.
- Additionally, check your repo after building
  ```bash
  flatpak run --command=flatpak-builder-lint repo repo
  ```
- Update `CHANGELOG.md` with notable changes.
- Maintain versioning scheme where relevant
- [Submit a pull request](https://github.com/flathub/org.munadi.Munadi/pull/new) to master branch

## Contributing (Project)

- Refer to [project's contributing guidelines](https://gitlab.com/munadi/munadi/-/blob/master/README.md#contributing)

## AI Contribution Policy

We try to be as clear as possible on AI agent, LLM and bot contributions to the project. AI-assisted contributions by humans are welcome, any other autonomous AI contributions including merge/pull requests, issues & comments will be rejected. This includes any variants of "Signed-off by `<agent's operator>`" i.e. human-operated agentic requests. We encourage both seasoned and new-comer (human) contributors to include `"Assisted by: "` footer whenever presenting any contributions on the project if using any assistances by AIs & LLMs.

---

## License

This project is licensed under the AGPL-3.0-or-later license. Licenses apply to individual tools used in this project. See the [LICENSE](https://gitlab.com/munadi/munadi/-/blob/master/LICENSE) file for details.

---

- **Homepage**: [munadi.org](https://munadi.org)
- **Bug Tracker**: [GitLab Issues](https://gitlab.com/munadi/munadi/-/issues) | [Flathub Issues](https://github.com/flathub/org.munadi.Munadi/issues)
- **Source Code**: [Source](https://gitlab.com/munadi/munadi) | [Flathub](https://github.com/flathub/org.munadi.Munadi)

---

*For historical context, see the [CHANGELOG](CHANGELOG.md).*
