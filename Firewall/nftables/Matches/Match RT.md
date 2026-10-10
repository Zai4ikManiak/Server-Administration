| Match Syntax | Examples |
| :---: | :--- |
| `nexthdr <proto>` | `rt nexthdr { udplite, ipcomp, udp, ah, sctp, esp, dccp, tcp, ipv6-icmp }`</br>`rt nexthdr 22`</br>`rt nexthdr != 33-45` |
| `hdrlength <length>` | `rt hdrlength 22`</br>`rt hdrlength != 33-45`</br>`rt hdrlength { 33, 55, 67, 88 }` |
| `type <type>` | `rt type 22`</br>`rt type != 33-45`</br>`rt type { 33, 55, 67, 88 }` |
| `seg-left <value>` | `rt seg-left 22`</br>`rt seg-left != 33-45`</br>`rt seg-left { 33, 55, 67, 88 }` |
