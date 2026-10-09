| Match Syntax | Examples |
| :---: | :--- |
| `dport <destination port>` | `udplite dport 22`</br>`udplite dport != 33-45`</br>`udplite dport { 33-55 }`</br>`udplite dport { telnet, http, https }`</br>`udplite dport vmap { 22 : accept, 23 : drop }`</br>`udplite dport vmap { 25:accept, 28:drop }` |
| `sport < source port>` | `udplite sport 22`</br>`udplite sport != 33-45`</br>`udplite sport { 33, 55, 67, 88 }`</br>`udplite sport { 33-55 }`</br>`udplite sport vmap { 25:accept, 28:drop }`</br>`udplite sport 1024 udplite dport 22` |
| `checksum <checksum>` | `udplite checksum 22`</br>`udplite checksum != 33-45`</br>`udplite checksum { 33, 55, 67, 88 }`</br>`udplite checksum { 33-55 }` |
