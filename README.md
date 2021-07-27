# beatrice-lan

Beatrice's main ethernet infrastructure is implemented as a mesh network
based on a Google Wifi router and associated access points.
The router WAN interface connects to WiFi and 4G gateways and internally
supports wired and wireless LAN.

The router implements a primary network (192.168.1.0/24) with SSID ```beatrice``` (password '95344958') and a 
secondary network (10.0.0.0/24) with SSID ```beatrice-guest``` (password 'pleaseletmein').
The secondary network has limited access to resources on the primary network.

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

| Name           | Device           | Interface | MAC               | IP            | Description     |
|:---------------|:-----------------|:----------|:------------------|:--------------|:----------------|
| helm           | JetWay PC        |           | 00:30:18:CB:C4:23 | 192.168.1.2   | Signal K server |
| victron        | Victron CCGX     | eth0      | 6C:EC:EB:C3:2B:7E | 192.168.1.3   | Victron Venus GX controller |
| lte-gateway    | Raspberry Pi 3B+ | eth0      |                   | 192.168.2.1   | LTE router (LAN port) |
|                |                  | eth1      |                   | DHCP          | LTE router (WAN port) |
|                |                  | wlan0     |                   | 192.168.4.1   | LTE router hotspot (SSID: beatrice-gw, hidden) |
| home-assistant | Raspberry Pi 3B+ | eth0      | B8:27:EB:7E:6F:5E | 192.168.1.99  | Home Assistant controller |
|                |                  | wlan0     |                   | 192.168.99.1  | Home Assistant hostspot (SSID: beatrice-ha, hidden) |
| moode          | Raspberry Pi 3   | eth0      | B8:27:EB:3E:48:44 | 192.168.1.11  | Audio player (wheelhouse) and DNLA server |
| saloon-tv      | Samsung          | wlan0     | 00:12:FB:26:2D:4A | DHCP          | Saloon TV
| saloon-tv-kodi | Raspberry Pi 4   | wlan0     | E4:5F:01:0B:A3:25 | 192.168.1.12  | Kodi player |
| desktop1       |                  | eth0      |                   |               | Helm PC |
|                |                  | wlan0     |                   |               | |
