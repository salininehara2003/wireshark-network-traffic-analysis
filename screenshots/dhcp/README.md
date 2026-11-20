
# DHCP Traffic Analysis

## Objective
To capture and analyze DHCP communication between a client and a DHCP server.

## Activities Performed
- Captured DHCP Request and DHCP ACK messages.
- Examined DHCP packet details.
- Identified client and server IP addresses.
- Investigated DHCP transaction information.

## Wireshark Display Filter
`dhcp`

## Captured Information
- Client Requested IP: 192.168.8.101
- DHCP Server: 192.168.8.1
- Client MAC: c0:e4:34:73:7c:05
- Client UDP Port: 68
- Server UDP Port: 67
- Transaction ID: 0x470bb77c

## Key Learning Outcomes
- Understood the purpose of DHCP.
- Identified DHCP Request and ACK messages.
- Learned how DHCP supports automatic IP configuration.
- Understood UDP ports 67 and 68.

## Observation
The complete DORA sequence was not captured. The analysis focuses on the observed Request and ACK messages.

## Evidence
This folder contains screenshots of:
- DHCP packet list.
- Expanded DHCP Request details.
- Expanded DHCP ACK details.
