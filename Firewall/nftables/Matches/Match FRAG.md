| Match Syntax | Examples |
| :---: | :--- |
| `nexthdr <proto>` | `frag nexthdr { udplite, comp, udp, ah, sctp, esp, dccp, tcp, ipv6-icmp, icmp }`</br>`frag nexthdr 6`</br>`frag nexthdr != 50-51` |
| `reserved <value>` | `frag reserved 22`</br>`frag reserved != 33-45`</br>`frag reserved { 33, 55, 67, 88 }` |
| `frag-off <value>` | `frag frag-off 22`</br>`frag frag-off != 33-45`</br>`frag frag-off { 33, 55, 67, 88 }` |
| `more-fragments <value>` | `frag more-fragments 0`</br>`frag more-fragments 0` |
| `id <value>` | `frag id 1`</br>`frag id 33-45` | 
