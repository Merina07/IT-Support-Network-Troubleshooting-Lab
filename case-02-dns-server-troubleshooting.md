# Case Study 02: DNS Server Troubleshooting

## Objective
Test the responsiveness of configured DNS servers.

## Environment
- Operating System: Kali Linux
- Virtualisation: Oracle VirtualBox
- Network interface: eth0

## Tools Used
- nslookup
- /etc/resolv.conf

## Test 1: DNS Server 8.8.8.8

Command:
nslookup example.com 8.8.8.8

Result:
The server returned IPv4 and IPv6 address records.

Status: Successful

## Test 2: DNS Server 4.4.4.4

Command:
nslookup example.com 4.4.4.4

Result:
The requests timed out, and no server could be reached.

Status: Unsuccessful during testing

Possible causes:
- DNS service unavailable at the destination
- Network filtering or blocked DNS traffic
- A network path or server issue

The exact cause was not established.

## Test 3: IPv6 DNS Server

Command:
nslookup example.com fd17:625c:f037:2::3

Result:
The server returned IPv4 and IPv6 address records.

Status: Successful

## Conclusion
Two tested DNS servers responded successfully.
The server at 4.4.4.4 did not respond during testing.

Further investigation would be needed to determine the
cause of the timeout.