# beatrice-lan

Beatrice's on-board ethernet network (192.168.1.0/24) is managed by
a Google Wifi router which provides a WAN gateway and supports wired
and wireless mesh networks.

Google WiFi Router
WAN IP: DHCP
LAN IP: STATIC 192.168.1.254

Google WiFi Point
LAN IP: 192.168.1.203

The router WAN interface connects at any one time to either a WiFi bridge
implemented by a Ubiquiti Bullet or a 4G LTE router implemented by a
Raspberry Pi.
Both of these gateway devices are configured to automatically assign the
router WAN port an IP address on the 192.168.2.0/24 subnet. 

The router assigns static IP addresses to a number of clients:

| Name        | Interface | MAC               | IP            | Description     |
| helm        | eth0      |                   | 192.168.1.2   | Signal K server |
| victron     | eth0      |                   | 192.168.1.3   | Victron Venus GX controller |
| lte-gateway |        | 
