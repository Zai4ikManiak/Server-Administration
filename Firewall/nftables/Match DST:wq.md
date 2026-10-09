| Match Syntax | Examples |
| :---: | :--- |
| `nexthdr <proto>` | `dst nexthdr { udplite, ipcomp, udp, ah, sctp, esp, dccp, tcp, ipv6-icmp }`</br>`dst nexthdr 22`</br>`dst nexthdr != 33-45` |
| `hdrlength <length>` | `dst hdrlength 22`</br>`dst hdrlength != 33-45`</br>`dst hdrlength { 33, 55, 67, 88 }` |
