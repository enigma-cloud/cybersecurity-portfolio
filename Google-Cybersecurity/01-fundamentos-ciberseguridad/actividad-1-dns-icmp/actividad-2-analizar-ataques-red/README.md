## Description

Analysis of a security incident on a travel agency's website. The web server received a large volume of TCP SYN requests from an unknown IP address, which caused the service to become saturated and stop responding (connection timeout error).

## Type of attack identified

**Denial of Service (DoS) — SYN Flood Attack**

- The attacker sends a large number of TCP SYN requests without completing the connection process (handshake).
- The server becomes overwhelmed keeping half-open connections, exhausting its resources.
- The website stops responding to legitimate users, generating timeout errors.

## Impact on the organization

- The sales website became inaccessible to employees.
- Service interruption and loss of productivity.
- Potential damage to the company's reputation with customers.

## Mitigation measures

- Temporary blocking of the attacker's IP address on the firewall.
- Configuration of SYN connection limits (SYN cookies) to protect the server.
- Continuous network traffic monitoring to detect anomalous patterns.

## Tools

- Packet sniffer (Wireshark)
- Wireshark TCP/HTTP log

## Contents

- Cybersecurity incident report (attack analysis)
