
# HTTP vs HTTPS Traffic Analysis

## Objective
To compare HTTP and HTTPS communication using Wireshark.

## Activities Performed
- Generated HTTP traffic using curl.
- Captured an HTTP GET request.
- Examined HTTP response headers.
- Followed the HTTP stream to inspect readable content.
- Generated HTTPS traffic.
- Captured TLS handshake and Application Data packets.

## Commands Executed
`curl http://neverssl.com`

`curl https://example.com`

## Wireshark Display Filters
`http`

`tls`

## HTTP Observations
- HTTP Method: GET
- Website: neverssl.com
- HTTP Version: 1.1
- Response Status: 200 OK
- Destination Port: 80

## HTTPS Observations
- Captured TLS 1.2 and TLS 1.3 traffic.
- Identified TLS handshake-related packets.
- Observed encrypted Application Data.

## Key Learning Outcomes
- Understood HTTP communication.
- Learned how HTTP requests and responses work.
- Understood the role of TLS in HTTPS.
- Compared readable HTTP content with encrypted HTTPS application data.

## Evidence
This folder contains screenshots of:
- HTTP packet list.
- Follow HTTP Stream output.
- HTTP request and response details.
- TLS traffic captured in Wireshark.
