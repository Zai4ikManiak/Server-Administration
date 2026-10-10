| Match Syntax | Examples |
| :---: | :--- |
| `dport <destination port>` | `sctp dport 22`</br>`sctp dport != 33-45`</br>`sctp dport { 33-55 }`</br>`sctp dport { telnet, http, https }`</br>`sctp dport vmap { 22 : accept, 23 : drop }`</br>`sctp dport vmap { 25:accept, 28:drop }` |
| `sport < source port>` | `sctp sport 22`</br>`sctp sport != 33-45`</br>`sctp sport { 33, 55, 67, 88 }`</br>`sctp sport { 33-55 }`</br>`sctp sport vmap { 25:accept, 28:drop }`</br>`sctp sport 1024 sctp dport 22` |
| `checksum <checksum>` | `sctp checksum 22`</br>`sctp checksum != 33-45`</br>`sctp checksum { 33, 55, 67, 88 }`</br>`sctp checksum { 33-55 }` |
| `vtag <tag>` | `sctp vtag 22`</br>`sctp vtag != 33-45`</br>`sctp vtag { 33, 55, 67, 88 }`</br>`sctp vtag { 33-55 }` |
| `chunk <type>` | `sctp chunk init exists`</br>`sctp chunk error missing` |
| `chunk <type> <field>` | `sctp chunk data tsn 0x23` |
