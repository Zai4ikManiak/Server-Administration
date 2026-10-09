| Match Syntax | Examples |
| :---: | :--- |
| `dport <destination port>` | `udp dport 22`</br>`udp dport != 33-45`</br>`udp dport { 33-55 }`</br>`udp dport { telnet, http, https }`</br>`udp dport vmap { 22 : accept, 23 : drop }`</br>`udp dport vmap { 25:accept, 28:drop }` |
| `sport < source port>` | `udp sport 22`</br>`udp sport != 33-45`</br>`udp sport { 33, 55, 67, 88 }`</br>`udp sport { 33-55 }`</br>`udp sport vmap { 25:accept, 28:drop }`</br>`udp sport 1024 udp dport 22` |
| `length <length>` | `udp length 6666`</br>`udp length != 50-65`</br>`udp length { 50, 65 }`</br>`udp length { 35-50 }` |
| `checksum <checksum>` | `udp checksum 22`</br>`udp checksum != 33-45`</br>`udp checksum { 33, 55, 67, 88 }`</br>`udp checksum { 33-55 }` |
