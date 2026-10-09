| Match Syntax | Examples |
| :---: | :--- |
| `type <type>` | `icmpv6 type { destination-unreachable, packet-too-big, time-exceeded, echo-request, echo-reply, mld-listener-query, mld-listener-report, mld-listener-reduction, nd-router-solicit, nd-router-advert, nd-neighbor-solicit, nd-neighbor-advert, parameter-problem, mld2-listener-report } ` |
| `code <packet_code>` | `icmpv6 code 4`</br>`icmpv6 code 3-66`</br>`icmpv6 code { 5, 6, 7 }` |
| `checksum <value>` | `icmpv6 checksum 12343`</br>`icmpv6 checksum != 11-343`</br>`icmpv6 checksum { 1111, 222, 343 }` |
| `id <value>` | `icmpv6 id 12343`</br>`icmpv6 id != 11-343`</br>`icmpv6 id { 1111, 222, 343 }` |
| `sequence <value>` | `icmpv6 sequence 12343`</br>`icmpv6 sequence != 11-343`</br>`icmpv6 sequence { 1111, 222, 343 }` |
| `mtu <value>` | `icmpv6 mtu 12343`</br>`icmpv6 mtu != 11-343`</br>`icmpv6 mtu { 1111, 222, 343 }` |
| `max-delay <value>` | `icmpv6 max-delay 33-45`</br>`icmpv6 max-delay != 33-45`</br>`icmpv6 max-delay { 33, 55, 67, 88 }` |
