| Match Syntax | Examples |
| :---: | :--- |
| `nexthdr <proto>` | `mh nexthdr { udplite, ipcomp, udp, ah, sctp, esp, dccp, tcp, ipv6-icmp }`</br>`mh nexthdr 22`</br>`mh nexthdr != 33-45` |
| `hdrlength <length>` | `mh hdrlength 22`</br>`mh hdrlength != 33-45`</br>`mh hdrlength { 33, 55, 67, 88 }` |
| `type <type>` | `mh type { binding-refresh-request, home-test-init, careof-test-init, home-test, careof-test, binding-update, binding-acknowledgement, binding-error, fast-binding-update, fast-binding-acknowledgement, fast-binding-advertisement, experimental-mobility-header, home-agent-switch-message }`</br>`mh type home-agent-switch-message`</br>`mh type != home-agent-switch-message` |
| `reserved <value>` | `mh reserved 22`</br>`mh reserved != 33-45`</br>`mh reserved { 33, 55, 67, 88 }` |
| `checksum <value>` | `mh checksum 22`</br>`mh checksum != 33-45`</br>`mh checksum { 33, 55, 67, 88 } ` |
