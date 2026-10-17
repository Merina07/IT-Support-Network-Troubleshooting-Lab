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
**Purpose:** To identify available network interface and inspect their IP Configuration.
```


### Test 2: Inspect the Routing Table

**Command:**
```bash
ip route
Purpose:
