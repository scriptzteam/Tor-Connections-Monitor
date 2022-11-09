# Tor-Connections-Monitor
Query Tor via its API to get connections count.

## Query Tor via its API

[relay-info.py](./relay-info.py) gives a summary of all connections, eg.:

```bash
sudo ./relay-info.py --address 127.0.0.1 --ctrlport 9051
```

gave here:

```console
 ORport 9051
 0.4.8.0-alpha-dev   uptime: 01:50:23   flags: Fast, Guard, Running, Stable, V2Dir, Valid

+------------------------------+-------+-------+
| Type                         |  IPv4 |  IPv6 |
+------------------------------+-------+-------+
| Inbound to our OR from relay |  2654 |   884 |
| Inbound to our OR from other |  5583 |    77 |
| Inbound to our ControlPort   |     1 |     2 |
| Outbound to relay OR         |  2209 |   576 |
| Outbound to relay non-OR     |       |       |
| Outbound exit traffic        |       |       |
| Outbound unknown             |     6 |       |
+------------------------------+-------+-------+
| Total                        | 10453 |  1539 |
+------------------------------+-------+-------+
```

For a monitoring of _exit_ connections use [exit-relay-info.py](./exit-relay-info.py):

```bash
sudo ./exit-relay-info.py --address 127.0.0.1 --ctrlport 9051
```

An open Tor control port is needed to query the Tor process via API.
Configure it in _torrc_, eg.:

```console
ControlPort 127.0.0.1:9051
ControlPort [::1]:9051
```

The [Stem](https://stem.torproject.org/index.html) python library is mandatory.
The latest version can be derived at:

```bash
git clone https://github.com/torproject/stem.git
export PYTHONPATH=$PWD/stem
```
