# Case Study 03: Windows Network Diagnostics

## Objective
To practise basic network troubleshooting on a Windows 11 laptop
using Command Prompt.

## Environment
- Operating System: Windows 11
- Network: Wi-Fi
- IPv4 Address: 192.168.1.9
- Default Gateway: 192.168.1.1

## Tests Performed

### 1. IP Configuration
Command:
ipconfig

Result:
Identified the laptop's IPv4 address, subnet mask, and default gateway.

### 2. Router Connectivity
Command:
ping -n 4 192.168.1.1

Result:
- Packets sent: 4
- Packets received: 4
- Packet loss: 0%

Conclusion:
The laptop successfully communicated with its default gateway.

### 3. External IP Connectivity
Command:
ping -n 4 1.1.1.1

Result:
- Packets sent: 4
- Packets received: 4
- Packet loss: 0%
- Average response time: 45 ms

Conclusion:
The laptop successfully reached the external IP address.

### 4. DNS Resolution
Command:
nslookup example.com

Result:
The DNS query succeeded using the DNS server reported as
dns.google at 8.8.8.8.

Conclusion:
The hostname example.com was successfully resolved to IP addresses.

### 5. Domain Connectivity
Command:
ping -n 4 example.com

Result:
- Packets sent: 4
- Packets received: 4
- Packet loss: 0%
- Minimum response time: 44 ms
- Maximum response time: 161 ms
- Average response time: 73 ms

Conclusion:
The domain resolved to an IPv4 address and responded to ping requests.

### 6. DNS Configuration Review
Command:
ipconfig /all

Result:
The Wi-Fi adapter listed these DNS server addresses:
- 8.8.8.8
- 4.4.4.4
- fe80::9a9d:b2ff:fe70:1020%22

Conclusion:
Multiple DNS server addresses were configured. This check alone
does not establish whether every listed server is reachable or reliable.

## Final Findings
The router connectivity, external IP connectivity, DNS lookup,
and domain ping tests succeeded.

No network fault was identified during these tests.
No configuration changes were made.
## Screenshots and Evidence

### 1. Windows IP Configuration
![Windows IP Configuration](Screenshots/windows-ip-configuration.png)

### 2. Connectivity and DNS Tests
![Connectivity and DNS Tests](Screenshots/windows-connectivity-and-dns.png)
## Skills Practised
- Windows Command Prompt
- IP configuration
- Default gateway testing
- Ping diagnostics
- DNS lookup
- Basic network troubleshooting
- Technical documentation
