# Technical Report: Network Traffic Analysis and Troubleshooting

## 1. Introduction

This project investigates real network traffic using Wireshark on a Windows 11 laptop. It focuses on analyzing common networking protocols, examining TCP connections, identifying port-scanning patterns and troubleshooting DNS resolution failures.

## 2. Project Environment

| Component | Details |
|---|---|
| Operating System | Windows 11 |
| Packet Analyzer | Wireshark |
| Network Scanner | Nmap 7.99.3 |
| Network Interface | Wi-Fi |
| Test Environment | Personal Wi-Fi network |

## 3. Protocol Analysis

### 3.1 ICMP Analysis

**Objective:** Examine ICMP Echo Request and Echo Reply messages.

**Activity:** Generated ping traffic and captured the packets using Wireshark.

**Display Filter:** `icmp`

**Observations:**
- Identified ICMP Echo Request packets.
- Identified ICMP Echo Reply packets.
- Examined packet size, TTL and response time.
- Observed communication between the local laptop and remote IP addresses.

**Result:** Successfully captured and analyzed ICMP communication.

### 3.2 DNS Analysis

**Objective:** Understand how domain names are resolved into IP addresses.

**Command:** `nslookup example.com`

**Display Filter:** `dns`

**Observations:**
- Captured DNS queries and responses.
- Identified A and AAAA record queries.
- Observed DNS communication using port 53.
- Identified returned IPv4 and IPv6 addresses.

**Result:** Successfully analyzed DNS name-resolution traffic.

### 3.3 ARP Analysis

**Objective:** Understand IPv4-to-MAC address resolution.

**Display Filter:** `arp`

**Observed ARP Request:**
- Sender IP: 192.168.8.1
- Target IP: 192.168.8.101
- Opcode: Request (1)

**Observed ARP Reply:**
- Sender IP: 192.168.8.101
- Sender MAC: c0:e4:34:73:7c:05
- Target IP: 192.168.8.1
- Opcode: Reply (2)

**Result:** Successfully identified ARP request and reply messages and examined the address-resolution process.

### 3.4 DHCP Analysis

**Objective:** Investigate DHCP communication between a client and a DHCP server.

**Display Filter:** `dhcp`

**Observed DHCP Messages:**
- DHCP Request
- DHCP ACK

**Captured Details:**
- Client IP requested: 192.168.8.101
- DHCP Server: 192.168.8.1
- Client MAC: c0:e4:34:73:7c:05
- Client source port: 68
- Server destination port: 67
- Transaction ID: 0x470bb77c

**Observations:**
The DHCP Request and ACK messages shared the same transaction ID. The complete DORA sequence was not captured.

**Result:** Successfully analyzed DHCP Request and ACK communication.

### 3.5 TCP Three-Way Handshake

**Objective:** Understand how TCP connections are established.

**Command:** `curl https://example.com`

**Display Filters:**
- `tcp.flags.syn == 1`
- `tcp.stream eq 40`

**Observed Handshake:**

| Packet | TCP Flag | Description |
|---|---|---|
| 813 | SYN | Client initiates connection |
| 815 | SYN-ACK | Server acknowledges request |
| 816 | ACK | Client acknowledges server |

**Captured TCP Parameters:**
- Client IP: 192.168.8.101
- Client Port: 42362
- Destination Port: 443
- TCP Stream: 40
- Window Size: 65535 bytes
- MSS: 1460 bytes
- SACK Permitted: Yes

**Result:** Successfully captured and analyzed the TCP three-way handshake.

### 3.6 HTTP vs HTTPS Analysis

**Objective:** Compare unencrypted HTTP communication with TLS-protected HTTPS communication.

**Commands:**
- `curl http://neverssl.com`
- `curl https://example.com`

**Display Filters:**
- `http`
- `tls`

**HTTP Observations:**
- Captured an HTTP GET request.
- Identified the Host and User-Agent headers.
- Observed HTTP/1.1 200 OK.
- Examined readable HTML content using Follow HTTP Stream.

**HTTPS Observations:**
- Captured TLS 1.2 and TLS 1.3 traffic.
- Identified TLS handshake-related packets.
- Observed encrypted Application Data.

**Result:** Demonstrated the difference between readable HTTP application content and TLS-protected HTTPS application communication.

## 4. Security Investigation: TCP SYN Port Scanning

**Objective:** Identify TCP SYN scanning patterns using Nmap and Wireshark.

**Target:** Personal Wi-Fi router (192.168.8.1)

**Command:**

`nmap -sS -Pn 192.168.8.1`

**Nmap Results:**

| Port | State | Service |
|---|---|---|
| 53 | Open | DNS |
| 80 | Open | HTTP |
| 443 | Open | HTTPS |
| 8888 | Open | Nmap service identification |

Additional results:
- 996 TCP ports were reported closed.
- The target host was reachable.

**Wireshark Filter:**

`tcp.flags.syn == 1 && tcp.flags.ack == 0`

**Observations:**
- Captured TCP SYN packets sent to multiple destination ports.
- Identified repeated connection-initiation attempts.
- Observed the packet pattern associated with TCP SYN scanning.

**Result:** Successfully performed an authorized scan against a personal router and analyzed the resulting traffic.

## 5. Network Troubleshooting: DNS Resolution Failure

**Objective:** Investigate DNS timeouts using an unavailable DNS resolver.

**Command:**

`nslookup example.com 192.0.2.1`

**Display Filter:** `dns`

**Test Environment:**
- Client IP: 192.168.8.104
- Test DNS Server: 192.0.2.1

**Observations:**
- DNS requests were sent to the test server.
- Repeated DNS request timeouts occurred.
- No matching DNS responses were observed.
- Other DNS communication with the normal resolver was also visible.

**Analysis:**

The test used 192.0.2.1, a reserved documentation address rather than an operational DNS resolver. Consequently, the test queries did not receive responses.

**Troubleshooting Recommendation:**

Use a reachable and authorized DNS resolver and verify successful domain resolution.

**Result:** Successfully demonstrated and analyzed an unanswered DNS query scenario.

## 6. Key Learning Outcomes

1. Developed practical knowledge of common TCP/IP protocols.
2. Gained experience capturing and analyzing network packets.
3. Understood DNS, ARP and DHCP communication.
4. Analyzed TCP connection establishment.
5. Compared HTTP and HTTPS traffic.
6. Identified TCP SYN scanning patterns.
7. Investigated DNS resolution failures.
8. Practiced using Wireshark display filters and Nmap.

## 7. Conclusion

This project provided practical experience in network traffic analysis, protocol investigation and basic network security monitoring.

Using Wireshark and Nmap, real network communication was captured and analyzed. The experiments improved understanding of networking protocols and demonstrated practical troubleshooting techniques relevant to Network Operations Centre (NOC) and Security Operations Centre (SOC) environments.

## 8. Tools and Technologies

- Wireshark
- Nmap
- Windows 11
- Command Prompt
- TCP/IP
- DNS
- ARP
- DHCP
- ICMP
- HTTP/HTTPS
- TLS

---

**Project:** Network Traffic Analysis and Troubleshooting with Wireshark

**Author:** Salini Nehara

**Specialization:** Network Technology

**University:** University of Sri Jayewardenepura
