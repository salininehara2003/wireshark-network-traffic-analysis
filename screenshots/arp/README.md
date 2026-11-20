
# ARP Traffic Analysis

## Objective
To investigate how ARP resolves IPv4 addresses into MAC addresses within a local network.

## Activities Performed
- Captured ARP Request and Reply packets.
- Examined Ethernet and ARP packet details.
- Identified sender and target IP addresses.
- Identified sender and target MAC addresses.

## Wireshark Display Filter
`arp`

## Captured Information
- Sender IP: 192.168.8.1
- Target IP: 192.168.8.101
- Reply Sender IP: 192.168.8.101
- Reply Sender MAC: c0:e4:34:73:7c:05
- Request Opcode: 1
- Reply Opcode: 2

## Key Learning Outcomes
- Understood IPv4-to-MAC address resolution.
- Differentiated ARP Request and ARP Reply messages.
- Learned how devices discover MAC addresses on a local network.

## Evidence
This folder contains screenshots of:
- ARP packet list.
- Expanded ARP Request details.
- Expanded ARP Reply details.
