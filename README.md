# Network Traffic Analysis and Troubleshooting with Wireshark

A practical networking project focused on capturing, analyzing, and troubleshooting real network traffic using Wireshark and Nmap on Windows 11.

## Project Overview

This project demonstrates practical network protocol analysis and basic security investigation using real network traffic captured from a personal Windows 11 laptop.

The project covers six networking experiments, TCP SYN port scanning, and DNS troubleshooting.

## Objectives

- Understand how common network protocols operate.
- Capture and analyze real network packets.
- Investigate TCP connection establishment.
- Compare HTTP and HTTPS communication.
- Identify TCP SYN port-scanning patterns.
- Troubleshoot DNS resolution failures.
- Develop practical NOC and SOC analysis skills.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Wireshark | Network packet capture and analysis |
| Nmap 7.99.3 | TCP port scanning |
| Windows 11 | Operating environment |
| Command Prompt | Network testing and commands |

## Practical Experiments

### 1. ICMP Traffic Analysis
- Generated ICMP traffic using ping.
- Identified Echo Request and Echo Reply packets.
- Examined TTL, packet size, and response time.

### 2. DNS Traffic Analysis
- Generated DNS queries using nslookup.
- Identified DNS queries and responses.
- Examined DNS records and UDP port 53.

### 3. ARP Traffic Analysis
- Captured ARP Request and Reply packets.
- Examined IPv4-to-MAC address resolution.
- Identified sender and target MAC addresses.

### 4. DHCP Traffic Analysis
- Captured DHCP Request and ACK messages.
- Examined UDP ports 67 and 68.
- Identified the assigned client IP and DHCP server.
- Documented the observed messages; the complete DORA sequence was not captured.

### 5. TCP Three-Way Handshake
- Captured TCP connection establishment.
- Identified SYN, SYN-ACK, and ACK packets.
- Examined sequence numbers, acknowledgment numbers, window size, and MSS.
- Used TCP stream filtering to isolate a connection.

### 6. HTTP vs HTTPS Analysis
- Captured an HTTP GET request and HTTP response.
- Examined readable HTTP headers and HTML content.
- Captured TLS traffic.
- Compared unencrypted HTTP communication with TLS-protected HTTPS communication.

## Security Investigation: TCP SYN Port Scanning

Performed an authorized SYN scan against my own Wi-Fi router using:

`nmap -sS -Pn 192.168.8.1`

Observed results:

| Port | State | Service |
|---|---|---|
| 53 | Open | DNS |
| 80 | Open | HTTP |
| 443 | Open | HTTPS |
| 8888 | Open | Nmap service identification |

- 996 additional TCP ports were reported closed.
- Captured TCP SYN packets using Wireshark.
- Identified connection attempts to multiple destination ports.

Wireshark display filter:

`tcp.flags.syn == 1 && tcp.flags.ack == 0`

## Network Troubleshooting: DNS Resolution Failure

Simulated an unavailable DNS resolver using:

`nslookup example.com 192.0.2.1`

Observations:
- DNS requests timed out.
- No matching DNS responses were observed.
- Wireshark was used to inspect the DNS traffic.

The test demonstrated how an unavailable DNS resolver can prevent successful domain-name resolution.

## Key Learning Outcomes

- Practical understanding of TCP/IP protocols.
- Network packet capture and interpretation.
- DNS, ARP, and DHCP troubleshooting.
- TCP connection analysis.
- HTTP and HTTPS security differences.
- Basic network reconnaissance detection.
- Wireshark display filter usage.
- Practical NOC/SOC investigation techniques.

## Project Environment

- Operating System: Windows 11
- Network: Personal Wi-Fi network
- Packet Analyzer: Wireshark
- Network Scanner: Nmap 7.99.3

## Author

**Salini Nehara**

Bachelor of Information and Communication Technology (Hons)  
Specialization: Network Technology  
University of Sri Jayewardenepura

---


