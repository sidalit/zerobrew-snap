<div align="center">

<img src="snap/gui/zerobrew.png" alt="zerobrew logo" width="128" />

# zerobrew

**Install, manage and run Homebrew command-line packages.**

[![zerobrew](https://snapcraft.io/zerobrew/badge.svg)](https://snapcraft.io/zerobrew)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64, arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [zerobrew](https://github.com/zerobrewhq/zerobrew), a fast Homebrew-compatible package manager written in Rust.

</div>

---

## Getting Started

<a href="https://snapcraft.io/zerobrew"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install zerobrew
zerobrew install jq
zerobrew run jq --version
zerobrew.zbx jq --version
```

Packages are installed into a private prefix. Use `zerobrew run` or `zerobrew.zbx` to launch them inside the snap. The formula's executable must have the same name as the formula for these upstream commands to find it.

## Configure

Package data and downloads live in `~/snap/zerobrew/common/data`; installed packages live in `~/snap/zerobrew/common/prefix`. Both survive snap updates. Initialization is automatic and does not edit your shell configuration. There are no `snap set` options.

To use the upstream command names:

```bash
sudo snap alias zerobrew zb
sudo snap alias zerobrew.zbx zbx
```

An optional Homebrew compatibility command is available as `zerobrew.brew`. Use `sudo snap alias zerobrew.brew brew` to name it `brew`. Do not use `zerobrew install-alias`, which writes beside the read-only executable.

For Brewfiles and other files on removable storage:

```bash
sudo snap connect zerobrew:removable-media
```

## Limitations

- This package supports confined command-line workloads from Linux bottles. Downloaded tools inherit the snap's permissions, and package compatibility varies by architecture. Some bottles retain fixed Linuxbrew paths or need additional post-install tools and may not work.
- Source builds, host compiler toolchains and migration from an existing Homebrew installation are unsupported. Ruby and development SDKs are not bundled. A formula without a suitable bottle may attempt a source build and fail.
- Host-wide installation, desktop integration, devices and service management are unavailable. Homebrew casks are macOS-only. Top-level hidden home directories and host configurations are not automatically accessible.
- Run packages through the snap commands; adding the private prefix to your host `PATH` bypasses the snap launcher and is unsupported. Use `zerobrew init --no-modify-path` if you explicitly initialize directories.
- Update the application with `sudo snap refresh zerobrew`; update installed packages with `zerobrew upgrade`.

## Build

```bash
git clone https://github.com/sidalit/zerobrew-snap.git
cd zerobrew-snap
sudo snap install snapcraft --classic
snapcraft pack
```

```bash
sudo snap install --dangerous ./zerobrew_*.snap
zerobrew --version
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/zerobrew-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/zerobrewhq/zerobrew/issues).

## License

Snap packaging: [MIT](LICENSE).
