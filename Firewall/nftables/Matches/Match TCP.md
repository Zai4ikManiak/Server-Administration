| Match Syntax | Examples |
| :---: | :--- |
| `dport <destination port>` | `tcp dport 22`</br>`tcp dport != 33-45`</br>`tcp dport { 33-55 }`</br>`tcp dport { telnet, http, https }`</br>`tcp dport vmap { 22 : accept, 23 : drop }`</br>`tcp dport vmap { 25:accept, 28:drop }` |
| `sport < source port>` | `tcp sport 22`</br>`tcp sport != 33-45`</br>`tcp sport { 33, 55, 67, 88 }`</br>`tcp sport { 33-55 }`</br>`tcp sport vmap { 25:accept, 28:drop }`</br>`tcp sport 1024 tcp dport 22` |
| `sequence <value>` | `tcp sequence 22`</br>`tcp sequence != 33-45` |
| `ackseq <value>` | `tcp ackseq 22`</br>`tcp ackseq != 33-45`</br>`tcp ackseq { 33, 55, 67, 88 }`</br>`tcp ackseq { 33-55 }` |
| `flags <flags>` | `tcp flags { fin, syn, rst, psh, ack, urg, ecn, cwr }`</br>`tcp flags cwr`</br>`tcp flags != cwr` |
| `window <value>` | `tcp window 22`</br>`tcp window != 33-45`</br>`tcp window { 33, 55, 67, 88 }`</br>`tcp window { 33-55 }` |
| `checksum <checksum>` | `tcp checksum 22`</br>`tcp checksum != 33-45`</br>`tcp checksum { 33, 55, 67, 88 }`</br>`tcp checksum { 33-55 }` |
| `urgptr <pointer>` | `tcp urgptr 22`</br>`tcp urgptr != 33-45`</br>`tcp urgptr { 33, 55, 67, 88 }` |
| `doff <offset>` | `tcp doff 8` |
