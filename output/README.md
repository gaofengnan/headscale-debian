# headscale

> Fork of [dariogriffo/headscale-debian](https://github.com/dariogriffo/headscale-debian) (MIT); the original packaging is by Dario Griffo. Served at [deb.gaofn.xyz](https://deb.gaofn.xyz) for Debian 12 (bookworm) and 13 (trixie).

Headscale is an open source, self-hosted implementation of the Tailscale
control server.

## Features

- Full "base" support of Tailscale's features
- Configurable DNS
- Node registration via web flow or pre-authenticated keys
- Taildrop (file sharing)
- Access control lists
- MagicDNS support

## Configuration

The service reads its configuration from `/etc/headscale/config.yaml`. Edit
it, then start the service:

```sh
sudo systemctl start headscale
sudo systemctl enable headscale
```

## Documentation

- Website: https://headscale.net
- Documentation: https://headscale.net/stable/
- Source: https://github.com/juanfont/headscale
