# Munadi

## Your Simple and Beautiful Athan App

Munadi is a simple yet powerful Athan app designed to be a companion in your daily life. It offers a
clean, beautiful interface free from advertisements and tracking, delivering precise prayer alerts
for any city worldwide. The app includes dual calendar support (Gregorian & Hijri), multiple
calculation methods, and the ability to view prayer schedules for any date - past or future. A range
of thoughtful settings allows you to tailor the experience to your personal needs.

**Features:**

- Prayer times for nearly any city around the globe
- Qibla direction for current location
- Countdown to the next prayer, also visible in tooltips
- View prayer times for past or future dates
- Support for various global calculation methods
- Flexible time format options
- Fine-tune prayer times and Hijri date offsets
- Option to assign a unique and custom athan for each prayer
- Individual control to enable, mute, or adjust athan volumes
- Lightweight design with no advertisements or tracking
- Automatic switching between Dark and Light themes
- Customizable UI visual effects
- Dynamic wallpapers that reflect the time of prayer
- Language choices from Arabic and Bangla, with complete RTL layout support
- Convenient system-tray support

## Screenshots

### Version 26.11

<div style="overflow-x: auto; white-space: nowrap;">

| ![Main Page - Fajr](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/fajr.png) | ![Main Page - Sunrise](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/sunrise.png) | ![Main Page - Dhuhr](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/dhuhr.png) | ![Main Page - Asr](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/asr.png) | ![Main Page - Maghrib](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/maghrib.png) | ![Main Page - Isha](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/isha.png) |
| :------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------: |
|                                             Fajr                                             |                                              Sunrise                                               |                                             Dhuhr                                              |                                            Asr                                             |                                              Maghrib                                               |                                             Isha                                             |

| ![Material Light Theme](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/material-light.png) | ![Material Dark Theme](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/material-dark.png) | ![Settings Page - Light](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/settings-1.png) | ![Settings Page - Dark](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/settings-2.png) |
| :--------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------: |
|                                               Material Light                                               |                                              Material Dark                                               |                                          Settings Page (Dark)                                           |                                         Settings Page (Light)                                          |

| ![Tray Menu](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/tray-menu.png) | ![Tray Tooltip](https://gitlab.com/munadi/munadi/-/raw/master/screenshots/2611/tray-tooltip.png) |
| :----------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------: |
|                                         Tray Menu                                          |                                             Tooltip                                              |

</div>

---

> [!NOTE]
> This repository holds only the flathub manifest and flatpak related contents. For full project
> details and building the app from source, go to [project home](https://gitlab.com/munadi/munadi).

## Status (Flatpak)

[![Build pipeline](https://github.com/flathub-infra/vorarbeiter/actions/workflows/build.yml/badge.svg)](https://github.com/flathub-infra/vorarbeiter/actions/workflows/build.yml)

Supported Architectures:

- x86_64
- aarch64

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
# Replace VER with the file's version, e.g. Munadi-26.11.run
sh Munadi-<VER>.run -q
```

Alternatively:

```bash
sh ./Munadi-<VER>.run
```

and follow instructions.

## Building from Source

Clone the repo:

```bash
git clone --recursive --depth 1 https://github.com/flathub/org.munadi.Munadi.git ./munadi_flathub \
  && cd ./munadi_flathub
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

## Versioning

Version format follows
[upstream convention](https://gitlab.com/munadi/munadi/-/blob/master/README.md#versioning).
Follow-up published changes on this repository add revision number to upstream version:
`<upstream>-<revision>` (e.g. `22.04-1` after `22.04` while the project is at `22.04`).

## Bug Reports

First of all, see if the issue you're facing already exists on the issue board. If not, follow these
workflow before reporting bugs:

1. Run `flatpak update --appstream` and `flatpak update -y`
2. Remove old configs and caches:

```bash
mv ~/.var/app/org.munadi.Munadi{,.bak}
```

3. Run from terminal:

```bash
flatpak run \
  --command=munadi \
  --env=QT_LOGGING_RULES='*.debug=true;qt.*.info=true;kf.*.debug=false;qt.qml.import=true' \
  org.munadi.Munadi > munadi-log.txt 2>&1
```

and try reproducing the issues.

If issues persist, [open an issue on project home](https://gitlab.com/munadi/munadi/-/work_items)
with `munadi.log`. Explain as detail as possible with your current app version and relevant details.

## Contributing

- Validate your manifest:

  ```bash
  flatpak run --command=flatpak-builder-lint org.flatpak.Builder manifest /path/to/your/manifest
  ```

  > [!NOTE] Make sure your manifest uses the
  > [latest tagged commit of the project](https://gitlab.com/munadi/munadi/-/tags) as the source. Do
  > not use other commits as those are not guaranteed to be stable.

- Then your AppStream metainfo:

  ```bash
  flatpak run --command=flatpak-builder-lint org.flatpak.Builder metainfo /path/to/your.metainfo.xml
  ```

- Then test build and install [following the recommended workflow](#building-from-source). Replace
  with your manifest.

- Additionally, check your repo after building

  ```bash
  flatpak run --command=flatpak-builder-lint repo repo
  ```

- Update `CHANGELOG.md` with notable changes.

- Maintain versioning scheme where relevant

- [Submit a pull request](https://github.com/flathub/org.munadi.Munadi/pull/new) to master branch

## Contributing (Project)

- Refer to
  [project's contributing guidelines](https://gitlab.com/munadi/munadi/-/blob/master/README.md#contributing)

## AI Contribution Policy

We aim to be transparent about contributions from AI agents, LLMs, and bots. AI-assisted
contributions by humans are welcome. Any other autonomous AI contributions — including merge/pull
requests, issues, and comments — will be rejected. This includes any "Signed-off-by:
`<agent's operator>`" variants, i.e. human-operated agentic submissions. Human contributors are
encouraged to include an "Assisted by: " footer in any contribution that involved AI or LLM
assistance.

## License

This project is licensed under the AGPL-3.0-or-later license. Licenses apply to individual tools used in this project. See the
[LICENSE](https://gitlab.com/munadi/munadi/-/blob/master/LICENSE) file for details, and
[Acknowledgements](https://gitlab.com/munadi/munadi/-/blob/master/README.md#acknowledgements) for
licenses for used libraries.

### Contributors

- **Flathub Maintainer:** Hasan Esa [@HasanEsa](https://github.com/HasanEsa)
- **Project Author:** AA [@hakpw](https://gitlab.com/hakpw)
- me00001 [@me00001](https://github.com/me00001)
- Sabri Ünal [@yakushabb](https://github.com/yakushabb)
- Timothée Ravier [@travier](https://github.com/travier)

- **Homepage**: [munadi.org](https://munadi.org)
- **Bug Tracker**: [Issues](https://gitlab.com/munadi/munadi/-/issues) |
  [Flathub Issues](https://github.com/flathub/org.munadi.Munadi/issues)
- **Source Code**: [Source](https://gitlab.com/munadi/munadi) |
  [Flathub](https://github.com/flathub/org.munadi.Munadi)

---

_For historical context, see the [CHANGELOG](CHANGELOG.md)._
