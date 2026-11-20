
# DNS Resolution Failure Investigation

## Objective
To investigate DNS request timeouts using Wireshark.

## Scenario
A test DNS resolver is unavailable, preventing successful domain name resolution.

## Command Executed
`nslookup example.com 192.0.2.1`

## Test Configuration
- Client IP: 192.168.8.104
- Test DNS Server: 192.0.2.1

## Wireshark Display Filter
`dns`

## Observations
- Multiple DNS queries were sent to 192.0.2.1.
- No matching DNS responses were observed.
- Command Prompt displayed repeated DNS request timeouts.
- Other DNS communication with the normal resolver was also visible.

## Analysis
The address 192.0.2.1 is a reserved documentation address, not an operational DNS server. Therefore, the test requests did not receive responses.

## Troubleshooting Recommendation
Use a reachable and authorized DNS resolver and verify successful domain resolution.

## Key Learning Outcomes
- Understood DNS resolution failures.
- Identified unanswered DNS queries.
- Learned how to investigate DNS timeouts using Wireshark.
- Practiced basic network troubleshooting.

## Evidence
This folder contains screenshots of:
- Command Prompt DNS timeout results.
- Wireshark DNS query packets.
- DNS failure analysis.
