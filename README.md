# wg-info
Better wireguard status script

This script allows you to actually know, which peer in the `wg show` output is which by assigning them a name.
Also you can see, which peers are actually online as `wg-info` will ping them and set the color (red/green) accordingly.
To save time, this is done for all the peers in parallel.

The output is colored (if writing to a tty or explicitly requested) using terminal sequences, HTML or be just plain text.

## Usage

```
wg-info [-h] [--html] [--tty] [--ping] [-i INTERFACE]

```

Possible parameters:

* `tty`: Force terminal colors even when writing to a pipe
* `html`: Use HTML for coloring (useful for building a VPN status page)
* `ping`: Ping the peers and set the their color accordingly

## Config
For each interface, `wg-info` expects the configuration in `/etc/wireguard/[INTERFACE].conf`.
The config is the normal `wg-quick` syntax.
The name is added as a comment as `wg-quick` doesn't like surplus config entries.
The first IP address in the `AllowedIPs` will be used to ping the host.

```ini
[Peer]
# Name = The very secret node in antarctica
PublicKey = [...]
PresharedKey = [...]
AllowedIPs = 10.127.3.131/32, fdf3:3::131/128
```

## Screenshot

![wg-info](https://user-images.githubusercontent.com/725608/96891877-60ada580-1489-11eb-9f6c-f55f11691f54.png)
