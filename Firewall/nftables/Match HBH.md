| Match Syntax | Examples |
| :---: | :--- |
| `nexthdr <proto>` | `hbh nexthdr { udplite, comp, udp, ah, sctp, esp, dccp, tcp, icmpv6 }`</br>`hbh nexthdr 22`</br>`hbh nexthdr != 33-45` |
| `hdrlength <length>` | `hbh hdrlength 22`</br>`hbh hdrlength != 33-45`</br>`hbh hdrlength { 33, 55, 67, 88 }` | 
