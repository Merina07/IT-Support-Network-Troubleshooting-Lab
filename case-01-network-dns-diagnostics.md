# Case Study 01: Network Connectivity and DNS Diagnostics

## 1. Objective

To investigate network connectivity, routing, and DNS resolution in Kali Linux using command-line troubleshooting tools.

## 2. Environment

- **Operating System:** Kali Linux
- **Virtualization:** Oracle VirtualBox
- **Network Interface:** `eth0`

## 3. Tools Used

- `ping`
- `ip addr`
- `ip route`
- `nslookup`
- `getent`
- `cat /etc/resolv.conf`

## 4. Initial Network Assessment

### Command 1: Check Network Interfaces

```bash
ip addr
Purpose: To identify available network interfaces and inspect their IP configuration.

### Command 2: Check Routing Table
```bash
ip route

Purpose: To inspect the routing table and identify the default gateway.

## 5. Loopback Connectivity Test

Command:

ping -c 4 127.0.0.1

Purpose: To verify local TCP/IP loopback connectivity.

Result:

Packets sent: 4
Packets received: 4
Packet loss: 0%

Finding: The loopback connectivity test completed successfully.

6. External Connectivity Test

Command:

ping -c 4 1.1.1.1

Purpose: To test connectivity to an external IP address without relying on DNS resolution.

Result:

Packets sent: 4
Packets received: 4
Packet loss: 0%

Finding: The external IP connectivity test was successful.

7. Gateway Connectivity Test

Command:

ping -c 4 10.0.2.2

Purpose: To test connectivity to the specified gateway address.

Result:

Packets sent: 4
Packets received: 4
Packet loss: 0%

Finding: The tested gateway address responded successfully.

8. Additional IP Connectivity Test

Command:

ping -c 4 4.4.4.4

Purpose: To test whether the specified IP address responds to ICMP requests.

Result:

Packets sent: 4
Packets received: 0
Packet loss: 100%

Finding: No replies were received. This result alone does not confirm that the destination server is offline.

9. DNS Resolution Tests
Test A: Google DNS Server

Command:

nslookup example.com 8.8.8.8

Purpose: To test DNS resolution using the specified DNS server.

Result: DNS resolution completed successfully.

Finding: The DNS server returned a response for example.com.

Test B: Alternative DNS Server

Command:

nslookup example.com 4.4.4.4

Purpose: To test DNS resolution using the alternative DNS server.

Result: The request timed out.

Finding: The DNS request did not receive a response within the timeout period. The exact cause was not confirmed.

Test C: IPv6 DNS Server

Command:

nslookup example.com fd17:625c:f037:2::3

Purpose: To test DNS resolution using the specified IPv6 DNS server.

Result: DNS resolution completed successfully.

Finding: The tested IPv6 DNS server returned a response.

10. DNS Configuration and System Resolution
Test A: Inspect DNS Configuration

Command:

cat /etc/resolv.conf

Purpose: To inspect the DNS server entries configured for name resolution.

Observed DNS servers:

8.8.8.8
4.4.4.4
fd17:625c:f037:2::3

Finding: The configuration contained multiple DNS server entries.

Test B: Resolve Google Hostname

Command:

getent hosts google.com

Purpose: To check hostname resolution through the system's name service configuration.

Result: IPv6 address information was returned.

Finding: The system successfully returned address information for google.com.

Test C: Resolve Google IPv4 Address

Command:

getent ahostsv4 google.com

Purpose: To retrieve IPv4 address information for google.com.

Result: An IPv4 address, 142.251.43.238, was returned.

Finding: The system returned IPv4 address information.

Test D: Resolve Example Domain

Command:

getent hosts example.com

Purpose: To check hostname resolution for example.com.

Result: Two IPv6 addresses were returned.

Finding: The system returned IPv6 address information for the domain.

11. Screenshots and Evidence
Screenshot 1: Loopback and External Connectivity

Screenshot 2: DNS Timeout and Routing

Screenshot 3: DNS Server Comparison

Screenshot 4: DNS Configuration and Gateway Test

12. Troubleshooting Analysis and Conclusion
Findings
Loopback connectivity was successful.
External connectivity to 1.1.1.1 was successful.
The tested gateway address responded successfully.
The ping test to 4.4.4.4 received no replies.
DNS resolution through 8.8.8.8 was successful.
DNS resolution through the tested IPv6 DNS server was successful.
DNS requests to 4.4.4.4 timed out.
System hostname resolution returned IPv4 and IPv6 address information.
ip addr
