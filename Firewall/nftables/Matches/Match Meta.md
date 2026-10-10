| Match Syntax | Examples |
| :---: | :--- |
| **meta Packet Info Selector** | |
| `pkttype <type>` | `meta pkttype broadcast`</br>`meta pkttype != broadcast`</br>`meta pkttype { broadcast, unicast, multicast }` |
| `length <length>` | `meta length 1000`</br>`meta length != 1000`</br>`meta length > 1000`</br>`meta length 33-45`</br>`meta length != 33-45`</br>`meta length { 33, 55, 67, 88 }`</br>`meta length { 33-55, 67-88 }` |
| `protocol <protocol>` | `meta protocol ip`</br>`meta protocol != ip`</br>`meta protocol { ip, arp, ip6, vlan }` |
| `nfproto <protocol>` | `meta nfproto ipv4`</br>`meta nfproto != ipv6`</br>`meta nfproto { ipv4, ipv6 }` |
| `l4proto <protocol>` | `meta l4proto 22`</br>`meta l4proto != 233`</br>`meta l4proto 33-45`</br>`meta l4proto { 33, 55, 67, 88 }`</br>`meta l4proto { 33-55 }` |
| **Matching by interface** | |
| `iif <input interface index>` | `meta iif eth0`</br>`meta iif != eth0` |
| `iifname <input interface name>` | `meta iifname "eth0"`</br>`meta iifname != "eth0"`</br>`meta iifname { "eth0", "lo" }`</br>`meta iifname "eth*"` |
| `iiftype <input interface type>` | `meta iiftype { ether, ppp, ipip, ipip6, loopback, sit, ipgre }`</br>`meta iiftype != ether`</br>`meta iiftype ether` |
| `iifkind` | |
| `iifgroup <input group>` | `meta iifgroup 0`</br>`meta iifgroup != 0`</br>`meta iifgroup default`</br>`meta iifgroup != default`</br>`meta iifgroup { default }`</br>`meta iifgroup { 11,33 }`</br>`meta iifgroup { 11-33 }` |
| `oif <output interface index>` | `meta oif lo`</br>`meta oif != lo`</br>`meta oif { eth0, lo }` |
| `oifname <output interface name>` | `meta oifname "eth0"`</br>`meta oifname != "eth0"`</br>`meta oifname { "eth0", "lo" }`</br>`meta oifname "eth*"` |
| `oiftype <output interface type>` | `meta oiftype { ether, ppp, ipip, ipip6, loopback, sit, ipgre }`</br>`meta oiftype != ether`</br>`meta oiftype ether` |
| `oifkind` | |
| `oifgroup <group>` | `meta oifgroup 0`</br>`meta oifgroup != 0`</br>`meta oifgroup default`</br>`meta oifgroup != default`</br>`meta oifgroup { default }`</br>`meta oifgroup { 11,33 }`</br>`meta oifgroup { 11-33 }` |
| `ibrname` | |
| `obrname` | |
| `ibrvproto` | |
| `ibrpvid` | |
| `sdif` | |
| `sdifname` | |
| **Matching by packet mark, routing class and realm** | |
| `mark [set]` | `meta mark 0x4`</br>`meta mark 0x00000032`</br>`meta mark and 0x03 == 0x01`</br>`meta mark and 0x03 != 0x01`</br>`meta mark != 0x10`</br>`meta mark or 0x03 == 0x01`</br>`meta mark or 0x03 != 0x01`</br>`meta mark xor 0x03 == 0x01`</br>`meta mark xor 0x03 != 0x01`</br>`meta mark set 0xffffffc8 xor 0x16`</br>`meta mark set 0x16 and 0x16`</br>`meta mark set 0xffffffe9 or 0x16`</br>`meta mark set 0xffffffde and 0x16`</br>`meta mark set 0x32 or 0xfffff`</br>`meta mark set 0xfffe xor 0x16` |
| `priority [set] <priority>` | `meta priority none`</br>`meta priority 0x1:0x1`</br>`meta priority 0x1:0xffff`</br>`meta priority 0xffff:0xffff`</br>`meta priority set 0x1:0x1`</br>`meta priority set 0x1:0xffff`</br>`meta priority set 0xffff:0xffff` |
| `rtclassid <class>` | `meta rtclassid cosmos` |
| **Matching by socket UID / GID** | |
| `skuid <user id>` | `meta skuid { bin, root, daemon }`</br>`meta skuid root`</br>`meta skuid != root`</br>`meta skuid lt 3000`</br>`meta skuid gt 3000`</br>`meta skuid eq 3000`</br>`meta skuid 3001-3005`</br>`meta skuid != 2001-2005`</br>`meta skuid { 2001-2005 }` |
| `skgid <group id>` | `meta skgid { bin, root, daemon }`</br>`meta skgid root`</br>`meta skgid != root`</br>`meta skgid lt 3000`</br>`meta skgid gt 3000`</br>`meta skgid eq 3000`</br>`meta skgid 3001-3005`</br>`meta skgid != 2001-2005`</br>`meta skgid { 2001-2005 }` |
| **Matching by time** | |
| `time` | |
| `day` | |
| `hour` | |
| **Matching by security selectors** | |
| `cpu <cpu index>` | `meta cpu 1`</br>`meta cpu != 1`</br>`meta cpu 1-3`</br>`meta cpu != 1-2`</br>`meta cpu { 2,3 }`</br>`meta cpu { 2-3, 5-7 }` |
| `cgroup <group>` | `meta cgroup 1048577`</br>`meta cgroup != 1048577`</br>`meta cgroup { 1048577, 1048578 }`</br>`meta cgroup 1048577-1048578`</br>`meta cgroup != 1048577-1048578`</br>`meta cgroup { 1048577-1048578 }` |
| `secmark` | |
| `ipsec` | |
| **Matching by miscellaneous selectors** | |
| `nftrace` | |
| `random` | |
