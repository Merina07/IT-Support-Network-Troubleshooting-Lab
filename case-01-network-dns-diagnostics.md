# Case Study 01: Network Connectivity and DNS Diagnostics

## 1. Objective

The objective of this exercise was to investigate network connectivity, routing, and DNS resolution in Kali Linux using command-line troubleshooting tools.

The purpose was to understand how network diagnostic commands help identify connectivity and name-resolution issues and document the results accurately.

## 2. Environment

- Operating System: Kali Linux
- Virtualisation: Oracle VirtualBox
- Network Interface: `eth0`

## 3. Tools and Commands Used

| Tool or Command | Purpose |
|---|---|
| `ip addr` | Inspect network interfaces and IP addresses |
| `ip route` | Display routing information and the default gateway |
| `ping` | Test network connectivity |
| `nslookup` | Query DNS servers and inspect their responses |
| `getent` | Check hostname resolution through the system's name service configuration |
| `cat /etc/resolv.conf` | Display configured DNS resolver addresses |

## 4. Background

Network troubleshooting involves checking connectivity, routing, and DNS resolution to understand how a system communicates with other devices and services.

The `ping` command tests whether a destination responds to ICMP requests. The `ip addr` and `ip route` commands provide information about network interfaces and routing.

DNS translates domain names into IP addresses. Tools such as `nslookup` and `getent` help investigate name-resolution behaviour.

A successful test confirms that the tested operation worked at that time. A timeout means no response was received within the test period. A timeout alone does not establish the root cause of a problem.

## 5. Tests Performed

### Test 1: Inspect Network Interfaces

**Command:**

```bash
ip addr
```
**Purpose:** To identify available network interface and inspect their IP Configuration.
**Observed Result:** The command was used to inspect the network interface configuration.
**Finding:** This command helps identify network interfaces and their associated IP addresses.

### Test 2: Inspect the Routing Table

**Command:**
```bash
ip route
```
**Purpose:** To inspect routing information and identify the default gateway.

**Observed Result:** The routing table was inspected as part of the network diagnostic exercise.

**Finding:** The routing table helps show how network traffic is directed towards its destinations.

### Test 3: Test Loopback Connectivity

**Command:**
```bash
ping -c 4 127.0.0.1
```
**Purpose:** To verify local TCP/IP loopback connectivity.

**Observed Result:**
Packets sent: 4
Packets received: 4
Packet loss: 0%

**Status:** Successful

**Finding:** The loopback connectivity test completed successfully.

### Test 4: Test External IP Connectivity

**Command:**
```bash
ping -c 4 1.1.1.1
```
**Purpose:** To test connectivity to an external IP address without relying on DNS resolution.

**Observed Result:**

Packets sent: 4
Packets received: 4
Packet loss: 0%

**Status:** Successful

**Finding:** The external IP connectivity test was successful.

### Test 5: Test Gateway Connectivity

**Command:**
```bash
ping -c 4 10.0.2.2
```
**Purpose:** To test connectivity to the specified gateway address.

**Observed Result:**

Packets sent: 4
Packets received: 4
Packet loss: 0%

**Status:** Successful

**Finding:** The tested gateway address responded successfully.

### Test 6: Test Additional IP Connectivity

**Command:**
```bash

ping -c 4 4.4.4.4
```
**Purpose:** To test whether the specified IP address responds to ICMP requests.

**Observed Result:**

Packets sent: 4
Packets received: 0
Packet loss: 100%

**Status:** Unsuccessful during testing

**Finding:** No replies were received within the test period. This result alone does not confirm that the destination server is offline.

### Test 7: Query Google DNS Server

**Command:**

```bash
nslookup example.com 8.8.8.8
```

**Purpose:** To query example.com directly against the specified DNS server.

**Observed Result:** The query succeeded and returned DNS information for example.com.

**Status:** Successful

**Finding:** The specified DNS server responded to the query.

### Test 8: Query Alternative DNS Server

**Command:**
```bash

nslookup example.com 4.4.4.4

```

**Purpose:** To check whether the specified DNS server responds to a query for example.com.

**Observed Result:** The query timed out during testing.

**Status:** Unsuccessful during testing

**Finding:** No DNS response was received within the test period. The exact cause was not confirmed.

### Test 9: Query the IPv6 DNS Server

**Command:**
```bash

nslookup example.com fd17:625c:f037:2::3
```

**Purpose:** To query the specified IPv6 DNS server address.

**Observed Result:** The query succeeded and returned DNS information for example.com.

**Status:** Successful

**Finding:** The specified DNS server responded to the query.

## 6. DNS Configuration and System Resolution
## Test 1: Review DNS Resolver Configuration

**Command:**
```bash

cat /etc/resolv.conf
```

**Purpose:** To inspect the DNS server addresses listed in the resolver configuration.

**Observed Configuration:**

8.8.8.8
4.4.4.4
fd17:625c:f037:2::3

**Finding:** The resolver configuration listed two IPv4 DNS server addresses and one IPv6 DNS server address.

A listed address does not guarantee that the server is reachable or responding successfully.

## Test 2: Resolve Google Hostname

**Command:** getent hosts google.com

**Purpose:** To check hostname resolution through the system's name service configuration.

**Observed Result:** IPv6 address information was returned.

**Status:** Successful

**Finding:** The system returned address information for google.com.

## Test 3: Resolve Google IPv4 Address

**Command:**
```bash
getent ahostsv4 google.com
```

**Purpose:** To retrieve IPv4 address information for google.com.

**Observed Result:** The IPv4 address 142.251.43.238 was returned.

**Status:** Successful

**Finding:** The system returned IPv4 address information for google.com.

## Test 4: Resolve Example Domain

**Command:**
```bash
getent hosts example.com
```
**Purpose:** To check hostname resolution for example.com.

**Observed Result:** Two IPv6 addresses were returned.

**Status:** Successful

**Finding:** The system returned IPv6 address information for the domain.

## 7. Results Summary
Test	Result	Observation
Loopback connectivity	Successful	4 packets received
External IP connectivity to 1.1.1.1	Successful	4 packets received
Gateway connectivity to 10.0.2.2	Successful	4 packets received
Additional IP connectivity to 4.4.4.4	Unsuccessful	100% packet loss
DNS query to 8.8.8.8	Successful	DNS response received
DNS query to 4.4.4.4	Timed out	No response received
DNS query to fd17:625c:f037:2::3	Successful	DNS response received
System resolution for google.com	Successful	IPv6 information returned
IPv4 resolution for google.com	Successful	IPv4 address returned
System resolution for example.com	Successful	IPv6 information returned
## 8. Screenshots and Evidence

**The following screenshots document the network connectivity and DNS diagnostic exercises.**

**Screenshot 1:** Loopback and External Connectivity

This screenshot documents the loopback and external connectivity tests.

Screenshot 2: DNS Timeout and Routing

This screenshot documents the DNS timeout and routing checks performed during troubleshooting.

Screenshot 3: DNS Server Comparison

This screenshot documents the comparison of responses from different DNS server addresses.

Screenshot 4: DNS Configuration and Gateway

This screenshot documents the DNS configuration and gateway connectivity checks.

## 9. Troubleshooting Analysis

The network connectivity tests produced different results depending on the destination.

The loopback test, external IP test, and test to the specified gateway address succeeded. The ping test to 4.4.4.4 received no replies.

The DNS query to 8.8.8.8 succeeded, the query to 4.4.4.4 timed out, and the query to the specified IPv6 DNS server succeeded.

The system hostname-resolution tests also returned IPv4 and IPv6 address information.

These results indicate that basic network connectivity and DNS resolution were working for the tested destinations. However, the available results do not establish the cause of the unsuccessful tests involving 4.4.4.4.

Further investigation would be required to determine whether the issue relates to server availability, network filtering, routing, or another factor.

## 10. Conclusion

The exercise demonstrated how to inspect network interfaces and routing information, test connectivity, query specific DNS servers, and check system hostname resolution.

Most of the documented connectivity and DNS tests succeeded. The ping test to 4.4.4.4 received no replies, and the DNS query to that address timed out.

The exact cause of these unsuccessful tests was not established, and no permanent fix is claimed.

## 11. Skills Practised
Network connectivity testing
Network interface inspection
Routing table analysis
DNS troubleshooting
Using ping and nslookup
Reviewing DNS resolver configuration
IPv4 and IPv6 address resolution
Analysing command-line output
Technical documentation
## 12. Disclaimer

This report documents educational network troubleshooting exercises performed in a personal lab environment. The findings reflect the results recorded during testing. Possible causes are not presented as confirmed diagnoses.
