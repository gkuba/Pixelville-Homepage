# Pixelville Homepage

[Homepage](https://gethomepage.dev) dashboard config for a home lab, run as a Dockge stack.

## Layout

- `compose.yaml`: the stack. Network values come from `.env`.
- `config/`: Homepage config (`services.yaml`, `widgets.yaml`, `settings.yaml`, `bookmarks.yaml`, `custom.css`).
- `images/`: favicon and the two fonts the theme uses (served at `/images/`).
- `env.example`: every value the repo leaves out. Copy it to `.env` and fill it in.

## Setup

1. Create the stack in Dockge and paste `compose.yaml`.
2. Fill the Dockge `.env` box from `env.example`.
3. Copy `config/` and `images/` to `/opt/stacks/<stack>/config` and `/opt/stacks/<stack>/images`.
4. Deploy.

## Where the removed values go

| Variable | What to put |
|---|---|
| `HOMEPAGE_ALLOWED_HOSTS` | `host:port` you open Homepage on |
| `DNS_SERVER`, `DNS_SEARCH_DOMAIN` | LAN DNS server and its search domain |
| `IP_PIXELGATE`, `IP_PIXELAI`, `IP_PIXELSTORE`, `IP_PIXEL`, `IP_PIXEL2`, `IP_PIXEL3` | LAN address of each host. Short names do not resolve inside the container, so `extra_hosts` maps them. |
| `HOMEPAGE_VAR_MODEM_HOST` | modem address used by the Comcast Modem tile |
| `HOMEPAGE_VAR_TPLINK_PATH` | the path after the port in the TP-Link controller URL |
| `HOMEPAGE_VAR_*_KEY`, `*_USER`, `*_PASS` | credentials from each service, kept in `.env` only |

## Notes

- Jellyfin 10.12 and newer needs `version: 2` on its widget.
- The calendar is a service tile, not a top bar widget.
- Single quote any `.env` value containing `$`.
