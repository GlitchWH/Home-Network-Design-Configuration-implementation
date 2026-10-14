# Home Network Design, Configuration, Implementaion and Connectivity Testing | Cisco Packet Tracer

This project simulates a home network in Cisco Packet Tracer. A cable splitter divides the incoming coaxial signal between a cable modem and a television, and the modem connects to a home wireless router serving two wired desktop computers and one Wi-Fi laptop. The router was configured with DHCP (limited to 10 clients) on a 192.168.0.1/24 LAN, a changed administrator password, and a WPA2 Personal secured 2.4 GHz wireless network. When the hostname skillsforall.srv failed to resolve, I traced the fault to a missing DNS configuration, since clients had valid IP addresses and could ping the gateway. Adding and configuring a DNS server resolved the issue. The project demonstrated that local gateway reachability, DNS resolution, and upstream internet access must be verified separately.

Skills: Networking fundamentals, DHCP, DNS, WLAN security, IP addressing, troubleshooting, Cisco Packet Tracer

**Author:** Waqas Hussain (GlitchWH)
**Course:** Computer Communication and Networking (CCN)
**Program:** Computer System Engineering, UET Peshawar
**Instructor:** Prof. Dr. Ihsan Ul Haq
**Tool:** Cisco Packet Tracer
# Home Network Design, Configuration and Connectivity Testing


## Overview

This project simulates a typical home network in which a single cable-provider connection supplies both internet and television. A cable splitter divides the coaxial signal between a cable modem and a television. The modem connects to the Internet port of a home wireless router, which provides Ethernet ports, Wi-Fi, and DHCP services to local devices.

## Objectives

- Connect the cable splitter to the cable modem and the television.
- Connect the cable modem to the router's Internet port.
- Connect two desktop computers to the router's LAN ports.
- Configure the router's DHCP pool and administrator password.
- Enable a 2.4 GHz WLAN named MyHome secured with WPA2 Personal.
- Connect a laptop to the WLAN.
- Configure DNS so that the hostname skillsforall.srv resolves.
- Test connectivity and document troubleshooting.

## Network Components

| Device | Connection | Role |
|---|---|---|
| Cable Splitter | Coaxial | Splits the provider signal between modem and TV |
| Cable Modem | Coaxial / Ethernet | Connects the provider signal to the router |
| Home Wireless Router | Ethernet / Wi-Fi | Provides routing, Wi-Fi, and DHCP |
| Office PC | Ethernet | Wired client; used to access the router GUI |
| Bedroom PC | Ethernet | Wired client using DHCP |
| Laptop | Wi-Fi | Wireless client on the MyHome network |
| Television | Coaxial | Receives the TV signal |
| DNS Server | Added during troubleshooting | Resolves skillsforall.srv |

## Topology

```
Cable Provider / Incoming Coaxial Signal
                 |
           Cable Splitter
            /          \
      Cable Modem     Television
            |
     Home Wireless Router
       /      |       \
  Office PC  Bedroom PC  Laptop (Wi-Fi)
```

## Physical Connections

| Source | Destination | Medium |
|---|---|---|
| Splitter, Coaxial1 | Cable Modem, Port 0 | Coaxial |
| Splitter, Coaxial2 | Television, Port 0 | Coaxial |
| Cable Modem, Port 1 | Router, Internet port | Copper straight-through |
| Office PC, FastEthernet0 | Router, GigabitEthernet 0/1 | Copper straight-through |
| Bedroom PC, FastEthernet0 | Router, GigabitEthernet 0/3 | Copper straight-through |
| Laptop | Router, 2.4 GHz WLAN | Wireless |

## Configuration Summary

| Parameter | Value |
|---|---|
| Router LAN IP address | 192.168.0.1 |
| Subnet mask | 255.255.255.0 |
| DHCP server | Enabled |
| DHCP starting address | 192.168.0.100 |
| Maximum DHCP users | 10 |
| Wireless band | 2.4 GHz |
| SSID | MyHome |
| Wireless security | WPA2 Personal |
| Administrator password | Changed from default |
| Test hostname | skillsforall.srv |

## Implementation Procedure

1. Connected the splitter to the cable modem and television using coaxial cable, and switched the television on.
2. Connected the cable modem to the router's Internet port, and both PCs to the router's LAN ports using copper straight-through cable.
3. Set the Office PC to DHCP and used its default gateway address to open the router's web interface.
4. Set the maximum number of DHCP users to 10 and changed the administrator password.
5. Enabled the 2.4 GHz radio, changed the SSID to MyHome, and enabled WPA2 Personal security.
6. Connected the laptop to MyHome using PC Wireless and configured the Bedroom PC for DHCP.
7. Tested connectivity by browsing to skillsforall.srv from the client devices.

## Troubleshooting

| Observation | Finding | Action |
|---|---|---|
| Browser displayed "Host Name Unresolved" for skillsforall.srv | Clients had IP addresses and gateways, but the DNS field was 0.0.0.0 | Added a DNS server and configured the router's DNS setting |
| Ping to the default gateway returned 4 replies | Local connectivity to the router was confirmed | Focused on name resolution rather than physical links |
| Router WAN fields showed 0.0.0.0 | No valid upstream lease was visible at that moment | Marked as an item for verification |
| skillsforall.srv later displayed the Packet Tracer welcome page | Name resolution worked after the DNS fix | Confirmed in the simulation |

## Results

- The intended topology was built using coaxial, Ethernet, and wireless connections.
- The router LAN was configured as 192.168.0.1/24 with DHCP limited to 10 clients.
- The MyHome WLAN was secured with WPA2 Personal.
- A wired client successfully pinged its default gateway.
- After the DNS fix, skillsforall.srv displayed the Cisco Packet Tracer welcome page.

## Key Takeaways

- An IP address and default gateway alone do not enable hostname-based browsing; DNS must also be available and correctly configured.
- Reachability of the local gateway and access to the upstream internet are separate checks.


## Security Notes

Default credentials should always be changed. On real equipment, use unique administrator and Wi-Fi passwords, WPA2-AES or WPA3 where supported, and keep router firmware up to date. Lab credentials are intentionally not listed in this repository.
passwords:
admin
mypassphrase!


## How to Run

1. Install Cisco Packet Tracer.
2. Open the SmallHomeNetworkForNatsumi.pkt file from this repository.
3. Run the simulation and browse to skillsforall.srv from any client device.
