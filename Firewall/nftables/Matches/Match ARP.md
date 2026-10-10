| Match Syntax | Examples |
| :---: | :--- |
| `ptype <value>` | `arp ptype 0x0800` |
| `htype <value>` | `arp htype 1`</br>`arp htype != 33-45`</br>`arp htype { 33, 55, 67, 88 }` |
| `hlen <length>` | `arp hlen 1`</br>`arp hlen != 33-45`</br>`arp hlen { 33, 55, 67, 88 } ` |
| `plen <length>` | `arp plen 1`</br>`arp plen != 33-45`</br>`arp plen { 33, 55, 67, 88 } ` |
| `operation <value>` | `arp operation { nak, inreply, inrequest, rreply, rrequest, reply, request }` |
