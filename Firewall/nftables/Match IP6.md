| Match Syntax | Examples |
| :---: | :--- |
| `dscp <value> ` | `ip6 dscp cs1`</br>`ip6 dscp != cs1`</br>`ip6 dscp 0x38`</br>`ip6 dscp != 0x20`</br>`ip6 dscp { cs0, cs1, cs2, cs3, cs4, cs5, cs6, cs7, af11, af12, af13, af21, af22, af23, af31, af32, af33, af41, af42, af43, ef }` |
| `flowlabel <label>` | `ip6 flowlabel 22`</br>`ip6 flowlabel != 233`</br>`ip6 flowlabel { 33, 55, 67, 88 }`</br>`ip6 flowlabel { 33-55 }` |
| `length <length>` | `ip6 length 232`</br>`ip6 length != 233`</br>`ip6 length 333-435`</br>`ip6 length != 333-453`</br>`ip6 length { 333, 553, 673, 838 }` |
| `nexthdr <header>` | `ip6 nexthdr { esp, udp, ah, comp, udplite, tcp, dccp, sctp, icmpv6 }`</br>`ip6 nexthdr esp`</br>`ip6 nexthdr != esp`</br>`ip6 nexthdr { 33-44 }`</br>`ip6 nexthdr 33-44`</br>`ip6 nexthdr != 33-44` |
| `hoplimit <hoplimit>` | `ip6 hoplimit 1`</br>`ip6 hoplimit != 233`</br>`ip6 hoplimit 33-45`</br>`ip6 hoplimit != 33-45`</br>`ip6 hoplimit { 33, 55, 67, 88 }`</br>`ip6 hoplimit { 33-55 }` |
| `saddr <ip source address>` | `ip6 saddr 1234:1234:1234:1234:1234:1234:1234:1234`</br>`ip6 saddr ::1234:1234:1234:1234:1234:1234:1234`</br>`ip6 saddr ::/64`ip6 saddr ::1 ip6 daddr ::2 |
| `daddr <ip destination address>` | `ip6 daddr 1234:1234:1234:1234:1234:1234:1234:1234`</br>`ip6 daddr != ::1234:1234:1234:1234:1234:1234:1234-1234:1234::1234:1234:1234:1234:1234` |
| `version <version>` | `ip6 version 6` |
