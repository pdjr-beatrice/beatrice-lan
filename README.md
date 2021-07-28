# beatrice-lan

Beatrice's ethernet infrastructure is implemented around a mesh network
based on a Google Wifi router and associated access points.

The router's WAN interface is configured by DHCP and connects at any one
time to a gateway device which allows the ship to Internet connectivity
through whatever mechanism satisfies immediate need.
Currently, hardware provides for connection to either a remote harbour
wireless hotspot or a 4/5G cellular network.

Wireless connectivity is implemented by a Ubiquiti Bullet external router
whilst cellular network connectivity is provided by a 4G LTE router implemented
on a Raspberry Pi with connected LTE modem (USB dongle) and associated
external antenna.

The Google router implements a LAN (192.168.1.0/24) on both wired and wireless
mesh interfaces: the wired interface connects to a gigabit ethernet switch
and the wireless interface presents two networks: a primary service with SSID
```beatrice``` and a secondary service (10.0.0.0/24) with SSID ```beatrice-guest```.
The secondary network has limited access to resources on the primary network.

Google WiFi Router (Wheelhouse)
WAN IP: DHCP
LAN IP: STATIC 192.168.1.254

Google WiFi Point (Saloon)
LAN IP: 192.168.1.203

A number of network clients implement critical network services and are assigned
static IP addresses by the router.

| Name           | Device           | Interface | MAC               | IP            | Description     |
|:---------------|:-----------------|:----------|:------------------|:--------------|:----------------|
| helm           | JetWay PC        | eth0      | 00:30:18:CB:C4:23 | 192.168.1.2   | Signal K controller (http://192.168.1.2:3000) |
| victron        | Victron CCGX     | eth0      | 6C:EC:EB:C3:2B:7E | 192.168.1.3   | Victron Venus GX controller (http://192.168.1.3) |
| lte-gateway    | Raspberry Pi 3B+ | eth0      |                   | 192.168.2.1   | LTE router (LAN port) |
|                |                  | eth1      |                   | DHCP          | LTE router (WAN port) |
|                |                  | wlan0     |                   | 192.168.4.1   | LTE router hotspot (SSID: beatrice-gw, hidden and open) |
| homeassistant  | Raspberry Pi 3B+ | eth0      | B8:27:EB:7E:6F:5E | 192.168.1.99  | Home Assistant controller |
|                |                  | wlan0     |                   | 192.168.99.1  | Home Assistant hostspot (SSID: beatrice-ha, hidden and open) |
| moode          | Raspberry Pi 3   | eth0      | B8:27:EB:3E:48:44 | 192.168.1.11  | Audio player (wheelhouse) and DNLA server |
| saloon-tv      | Samsung          | wlan0     | 00:12:FB:26:2D:4A | DHCP          | Saloon TV
| saloon-tv-kodi | Raspberry Pi 4   | wlan0     | E4:5F:01:0B:A3:25 | 192.168.1.12  | Kodi player |
| desktop1       |                  | eth0      |                   |               | Helm PC |
|                |                  | wlan0     |                   |               | |

##helm

##victron

##lte-gateway

##homeassistant
