| Match Syntax | Examples |
| :---: | :--- |
| `dport <destination port>` | `dccp dport 22`</br>`dccp dport != 33-45`</br>`dccp dport { 33-55 }`</br>`dccp dport { telnet, http, https }`</br>`dccp dport vmap { 22 : accept, 23 : drop }`</br>`dccp dport vmap { 25:accept, 28:drop }` |
| `sport < source port>` | `dccp sport 22`</br>`dccp sport != 33-45`</br>`dccp sport { 33, 55, 67, 88 }`</br>`dccp sport { 33-55 }`</br>`dccp sport vmap { 25:accept, 28:drop }`</br>`dccp sport 1024 dccp dport 22` |
| `type <type>` | `dccp type { request, response, data, ack, dataack, closereq, close, reset, sync, syncack }`</br>`dccp type request`</br>`dccp type != request` |

