
# TCP SYN Port Scanning Analysis

## Objective
To investigate TCP SYN scanning activity using Nmap and analyze the resulting network traffic using Wireshark.

## Tools Used
- Nmap 7.99.3
- Wireshark
- Windows 11

## Target
Personal Wi-Fi Router: 192.168.8.1

## Nmap Command
`nmap -sS -Pn 192.168.8.1`

## Observed Results

| Port | State | Service |
|---|---|---|
| 53 | Open | DNS |
| 80 | Open | HTTP |
| 443 | Open | HTTPS |
| 8888 | Open | Nmap service identification |

Additional Results:
- 996 TCP ports reported closed.
- Target host was reachable.

## Wireshark Display Filter
`tcp.flags.syn == 1 && tcp.flags.ack == 0`

## Key Learning Outcomes
- Understood TCP SYN scanning.
- Identified connection attempts to multiple destination ports.
- Learned how to recognize scanning patterns in packet captures.
- Practiced basic network reconnaissance investigation.

## Evidence
This folder contains screenshots of:
- Nmap scan results.
- Wireshark TCP SYN packet analysis.
