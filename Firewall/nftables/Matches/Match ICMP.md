| Match Syntax | Examples |
| :---: | :--- |
| `type <type>` | `icmp type { echo-reply, destination-unreachable, source-quench, redirect, echo-request, time-exceeded, parameter-problem, timestamp-request, timestamp-reply, info-request, info-reply, address-mask-request, address-mask-reply, router-advertisement, router-solicitation } ` |
| `code <packet_code>` | `icmp code 111`</br>`icmp code != 33-55`</br>`icmp code { 2, 4, 54, 33, 56 }` |
| `checksum <value>` | `icmp checksum 12343`</br>`icmp checksum != 11-343`</br>`icmp checksum { 1111, 222, 343 }` |
| `id <value>` | `icmp id 12343`</br>`icmp id != 11-343`</br>`icmp id { 1111, 222, 343 }` |
| `sequence <value>` | `icmp sequence 12343`</br>`icmp sequence != 11-343`</br>`icmp sequence { 1111, 222, 343 }` |
| `mtu <value>` | `icmp mtu 12343`</br>`icmp mtu != 11-343`</br>`icmp mtu { 1111, 222, 343 }` |
| `gateway <value>` | `icmp gateway 12343`</br>`icmp gateway != 11-343`</br>`icmp gateway { 1111, 222, 343 }` |
