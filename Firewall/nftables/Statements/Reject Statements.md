The following rule shows how to reject any traffic from the network:

```bash
reject with <protocol> type <type>
```

---
If you don't specify any reason, an ICMP/ICMPv6 port unreachable packet is sent to the origin.

You can narrow down this through the ct selector, so this only rejects traffic coming to the local machine which was not originated from us.

```bash
nft add rule filter input ct state new reject
```

---
Traffic can also be refected with a specific reason:

| ICMPv4 Reject Reason | Description |
| :---: | :--- |
| `net-unreachable` | Destination network unreachable |
| `host-unreachable` | Destination host unreachable |
| `prot-unreachable` |  Destination protocol unreachable |
| `port-unreachable` | Destination port unreachable (this is the default) |
| `net-prohibited` | Network administratively prohibited |
| `host-prohibited` | Host administratively prohibited |
| `admin-prohibited` | Communication administratively prohibited |

| ICMPv6 Reject Reason | Description |
| :--- | :---: |
| `no-route` | No route to destination |
| `admin-prohibited` | Communication with destination administratively prohibited |
| `addr-unreachable` | Address unreachable |
| `port-unreachable` | Port unreachable |

From the inet family, you can use an abstraction, the so-called icmpx, to reject the IPv4 and IPv6 traffic using one single rule.

| IMCPX Reason | ICMPv6 | ICMPv4 |
| :---: | :---: | :---: |
| `admin-prohibited` | `admin-prohibited` | `admin-prohibited` |
| `port-unreachable` | `port-unreachable` | `port-unreachable` |
| `no-route` | `no-route` | `net-unreachable` |
| `host-unreachable` | `addr-unreachable` | `host-unreachable` |

```bash
nft add rule filter input reject with icmp type host-unreachable
nft add rule ip6 filter input reject with icmpv6 type no-route
nft add rule inet filter input reject with icmpx type no-route
```
