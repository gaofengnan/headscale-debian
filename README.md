![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/gaofengnan/headscale-debian/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/gaofengnan/headscale-debian/latest/total)
![GitHub Release](https://img.shields.io/github/v/release/gaofengnan/headscale-debian)
![GitHub Release Date](https://img.shields.io/github/release-date/gaofengnan/headscale-debian?display_date=published_at)

# headscale for Debian

> Fork of [dariogriffo/headscale-debian](https://github.com/dariogriffo/headscale-debian) (MIT); the original packaging is by Dario Griffo. Served at [deb.gaofn.xyz](https://deb.gaofn.xyz) for Debian 12 (bookworm) and 13 (trixie).

This repository contains build scripts to produce the _unofficial_ Debian packages
(.deb) for [headscale](https://github.com/juanfont/headscale) hosted at [deb.gaofn.xyz](https://deb.gaofn.xyz)

Currently supported Debian distros are:
- Bookworm (v12)
- Trixie (v13)
- Forky (v14)
- Sid (testing)

Currently supported Ubuntu distros are:
- Jammy
- Noble
- Questing
- Resolute

**Upstream architectures:** amd64 and arm64 only (upstream also publishes its own .deb for these two architectures).

This is an unofficial community project to provide a package that's easy to
install on Debian. If you're looking for the headscale source code, see
[headscale](https://github.com/juanfont/headscale).

## Install/Update

### The Debian way

```sh
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.gpg -o /etc/apt/keyrings/deb.gaofn.xyz.gpg
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.sources -o /etc/apt/sources.list.d/deb.gaofn.xyz.sources
# Debian 12 (bookworm): fetch deb.gaofn.xyz-bookworm.sources instead
sudo apt update
sudo apt install -y headscale
```

### Manual Installation

1. Download the .deb package for your Debian version available on
   the [Releases](https://github.com/gaofengnan/headscale-debian/releases) page.
2. Install the downloaded .deb package.

```sh
sudo dpkg -i <filename>.deb
```
## Post-installation

After installing the package, complete the headscale setup:

1. Review the configuration at `/etc/headscale/config.yaml`.
2. Start the service:
   ```sh
   sudo systemctl start headscale
   ```
3. Enable it on boot:
   ```sh
   sudo systemctl enable headscale
   ```

The package automatically:
- Creates the `headscale` system user and group
- Creates `/var/lib/headscale` (state directory, owned by `headscale:headscale`, mode `750`)
- Ships `/etc/headscale/config.yaml` (owned by `root:headscale`, mode `640`)
- Installs the systemd service file

## Updating

To update to a new version, just follow any of the installation methods above. There's no need to uninstall the old version; it will be updated correctly.

## Building

### Build for single architecture
```sh
./build.sh <headscale_version> <build_version> <architecture>
# Example: ./build.sh 0.29.2 1 arm64
```

### Build for all architectures
```sh
./build.sh <headscale_version> <build_version> all
# Example: ./build.sh 0.29.2 1 all
```

## Roadmap

- [x] Produce a .deb package on GitHub Releases
- [ ] Set up a debian mirror for easier updates
- [x] Multi-architecture support (amd64, arm64)

## Disclaimer

- This repo is not open for issues related to headscale. This repo is only for _unofficial_ Debian packaging.
