# Case Study 01: Network Connectivity and DNS Diagnostics

## 1. Objective
Assess basic network connectivity, inspect routing information, test DNS resolution, and document the findings using Kali Linux.

## 2. Environment
- Operating System: Kali Linux
- Virtualization: Oracle VirtualBox
- Network Interface: eth0
- Tools: ping, ip addr, ip route, getent, nslookup

## 3. Tests Performed

### Test 1: Local Loopback
**Command:** `ping -c 4 127.0.0.1`

**Result:** 4 packets transmitted, 4 received, 0% packet loss.

**Finding:** The local loopback address responded successfully.

### Test 2: External Connectivity
**Command:** `ping -c 4 1.1.1.1`

**Result:** 4 packets transmitted, 4 received, 0% packet loss.

**Finding:** The external IP address responded to ping requests.

### Test 3: Default Gateway
**Command:** `ping -c 4 10.0.2.2`

**Result:** 4 packets transmitted, 4 received, 0% packet loss.

**Finding:** The default gateway responded successfully.

### Test 4: Ping to 4.4.4.4
**Command:** `ping -c 4 4.4.4.4`

**Result:** 4 packets transmitted, 0 received, 100% packet loss.

**Finding:** No ping replies were received. This does not prove the destination is offline.

### Test 5: DNS Query to 8.8.8.8
**Command:** `nslookup example.com 8.8.8.8`

**Result:** Successful DNS response.

**Finding:** The DNS query returned addresses for example.com.

### Test 6: DNS Query to 4.4.4.4
**Command:** `nslookup example.com 4.4.4.4`

**Result:** DNS query timed out.

**Finding:** No DNS response was received during the test. The cause remains unconfirmed.

### Test 7: DNS Query to Configured IPv6 Server
**Command:** `nslookup example.com fd17:625c:f037:2::3`

**Result:** Successful DNS response.

### Test 8: Inspect DNS Configuration
**Command:** `cat /etc/resolv.conf`

**Finding:** The configuration listed three DNS server addresses:
- `8.8.8.8`
- `4.4.4.4`
- `fd17:625c:f037:2::3`

### Test 9: Resolve Google Using the System Resolver
**Command:** `getent hosts google.com`

**Result:** An IPv6 address was returned.

### Test 10: Resolve Google to IPv4
**Command:** `getent ahostsv4 google.com`

**Result:** The IPv4 address `142.251.43.238` was returned.

### Test 11: Resolve example.com
**Command:** `getent hosts example.com`

**Result:** Two IPv6 addresses were returned.

## 4. Analysis

The default gateway and the external IP address 1.1.1.1 responded to ping requests. DNS resolution also succeeded through 8.8.8.8 and the configured IPv6 DNS server.

However, ping requests to 4.4.4.4 received no replies, and DNS queries to that address timed out.

The exact cause has not been established. Additional investigation would be required before identifying a root cause.

## 5. Conclusion

Basic network connectivity and domain-name resolution were working during the tests performed.

This exercise provided practical experience with:
- Linux networking commands
- IP addressing and routing
- Gateway connectivity testing
- DNS troubleshooting
- IPv4 and IPv6 resolution
- Technical documentation

No confirmed root cause or permanent fix is claimed.

## 6. Skills Practised
- Kali Linux command line
- Basic network diagnostics
- DNS resolution
- IPv4 and IPv6 fundamentals
- Troubleshooting analysis
- Technical report writing
