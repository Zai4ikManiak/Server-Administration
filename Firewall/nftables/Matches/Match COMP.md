| Match Syntax | Examples |
| :---: | :--- |
| `nexthdr <protocol>` | `comp nexthdr != esp`</br>`comp nexthdr { esp, ah, comp, udp, udplite, tcp, tcp, dccp, sctp }` |
| `flags <flags>` | `comp flags 0x0`</br>`comp flags != 0x33-0x45`</br>`comp flags { 0x33, 0x55, 0x67, 0x88 }` |
| `cpi <value>` | `comp cpi 22`</br>`comp cpi != 33-45`</br>`comp cpi { 33, 55, 67, 88 }` |
