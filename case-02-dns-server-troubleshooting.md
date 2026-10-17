# Case Study 02: DNS Server Troubleshooting

## 1. Objective

The objective of this exercise was to investigate DNS resolution
by querying different DNS servers, comparing their responses,
and reviewing the configured DNS server addresses.

The purpose was to understand how DNS troubleshooting helps
identify differences in server responsiveness and document
the results accurately.

## 2. Environment

- Operating System: Kali Linux
- Virtualisation: Oracle VirtualBox
- Network Interface: eth0

## 3. Tools and Commands Used

| Tool or Command | Purpose |
|---|---|
| `nslookup` | Query a DNS server and inspect its response |
| `cat /etc/resolv.conf` | Display configured DNS resolver addresses |
| `ping` | Test IP-level reachability when needed |

## 4. Background

The Domain Name System (DNS) translates domain names into IP
addresses so computers can locate network services.

During troubleshooting, different DNS servers can be queried
to compare their responses.

A successful response shows that the server answered that query.
A timeout means no response was received within the test period.
A timeout alone does not prove why the server failed to respond.

## 5. Tests Performed

### Test 1: Query DNS Server 8.8.8.8

**Command:**

```bash
nslookup example.com 8.8.8.8
```

**Purpose:**

To query `example.com` directly against the specified DNS server.

**Observed result:**

The query succeeded and returned IPv4 and IPv6 address records
for `example.com`.

**Status:** Successful

**Finding:**

The specified DNS server responded to this query and returned
address records for the requested domain.

### Test 2: Query DNS Server 4.4.4.4

**Command:**

```bash
nslookup example.com 4.4.4.4
```

**Purpose:**

To check whether the specified DNS server responded to a query
for `example.com`.

**Observed result:**

The query timed out during testing.

**Status:** Unsuccessful during testing

**Finding:**

No DNS response was received within the test period.

Possible explanations include a DNS service issue, network
filtering, or a connectivity problem. The available result
does not establish which explanation, if any, is correct.

No permanent fix is claimed.

### Test 3: Query the IPv6 DNS Server

**Command:**

```bash
nslookup example.com fd17:625c:f037:2::3
```

**Purpose:**

To query the specified IPv6 DNS server address.

**Observed result:**

The query succeeded and returned IPv4 and IPv6 address records
for `example.com`.

**Status:** Successful

**Finding:**

The specified DNS server responded to the query.

### Test 4: Review DNS Resolver Configuration

**Command:**

```bash
cat /etc/resolv.conf
```

**Purpose:**

To inspect the DNS server addresses listed in the resolver
configuration.

**Previously documented configuration:**

- `8.8.8.8`
- `4.4.4.4`
- `fd17:625c:f037:2::3`

**Finding:**

The resolver configuration listed two IPv4 DNS server addresses
and one IPv6 DNS server address.

A listed address does not guarantee that the server is reachable
or responding successfully.

> Keep this test only if you actually ran the command and
> confirmed these addresses during this exercise.

## 6. Results Summary

| DNS Server | Result | Observation |
|---|---|---|
| `8.8.8.8` | Successful | Returned address records |
| `4.4.4.4` | Timed out | No response received during testing |
| `fd17:625c:f037:2::3` | Successful | Returned address records |

## 7. Screenshots and Evidence

The following screenshots document the DNS troubleshooting
and network diagnostic exercises.

### Screenshot 1: DNS Timeout and Routing

This screenshot documents the DNS timeout and routing checks
performed during the troubleshooting exercise.

![DNS timeout and routing](Screenshots/dns-timeout-and-routing.jpeg)

### Screenshot 2: DNS Server Comparison

This screenshot documents the comparison of responses from
different DNS server addresses.

![DNS server comparison](Screenshots/dns-server-comparison.jpeg)

### Screenshot 3: DNS Configuration and Gateway

This screenshot documents the DNS configuration and gateway
checks associated with the troubleshooting exercise.

![DNS configuration and gateway test](Screenshots/dns-configuration-and-gateway-test.jpeg)

## 8. Troubleshooting Analysis

The tests produced different results for the DNS server addresses.

The query to `8.8.8.8` succeeded, the query to `4.4.4.4` timed
out, and the query to the specified IPv6 DNS server succeeded.

These results show why comparing DNS server responses can be
useful when investigating name-resolution problems.

However, the timeout does not establish whether the cause was
the DNS service, network filtering, routing, or another factor.

Additional tests would be required to isolate the cause.

## 9. Conclusion

The exercise demonstrated how to query specific DNS servers,
compare their responses, and review resolver configuration.

Two of the documented DNS queries succeeded, while the query
to `4.4.4.4` timed out.

The exact cause of the timeout was not established, and no
permanent fix is claimed.

## 10. Lessons Learned

- `nslookup` can query a specified DNS server.
- Comparing DNS responses helps identify differences in
  server responsiveness.
- DNS resolution and IP-level connectivity are different
  troubleshooting checks.
- A timeout is an observation, not a confirmed root cause.
- Technical reports should distinguish test results from
  possible explanations.

## 11. Skills Practised

- DNS troubleshooting
- Using `nslookup`
- Reviewing DNS resolver configuration
- Comparing DNS server responses
- Analysing command-line output
- Technical documentation

## 12. Disclaimer

This report documents educational troubleshooting exercises.
The findings reflect the results recorded during testing.
Possible causes are not presented as confirmed diagnoses.
