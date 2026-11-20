
# TCP Three-Way Handshake Analysis

## Objective
To understand how TCP connections are established using the three-way handshake.

## Activities Performed
- Generated HTTPS traffic using curl.
- Captured TCP connection establishment packets.
- Identified SYN, SYN-ACK and ACK messages.
- Examined TCP sequence and acknowledgment numbers.
- Investigated TCP window size and Maximum Segment Size (MSS).
- Isolated a TCP conversation using stream filtering.

## Wireshark Display Filters
`tcp.flags.syn == 1`

`tcp.stream eq 40`

## Captured Information
- Client IP: 192.168.8.101
- Client Port: 42362
- Destination Port: 443
- TCP Stream Index: 40
- Window Size: 65535 bytes
- MSS: 1460 bytes
- SACK Permitted: Yes

## Three-Way Handshake
1. SYN - Client initiates the connection.
2. SYN-ACK - Server acknowledges and responds.
3. ACK - Client acknowledges the server response.

## Key Learning Outcomes
- Understood TCP connection establishment.
- Identified TCP control flags.
- Learned the purpose of sequence and acknowledgment numbers.
- Understood TCP window size and MSS.

## Evidence
This folder contains screenshots of:
- TCP SYN packets.
- Expanded TCP packet details.
- Complete three-way handshake.
