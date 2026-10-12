| NAT Statements | Description |
| :---: | :--- |
| `dnat to <destination address>` | `dnat to 192.168.3.2`</br>`dnat to ct mark map { 0x00000014 : 1.2.3.4 }` |
| `snat to <ip source address>` | `snat to 192.168.3.2`</br>`snat to 2001:838:35f:1::-2001:838:35f:2:::100` |
| `masquerade [<type>] [to :<port>]` | `masquerade`</br>`masquerade persistent,fully-random,random`</br>`masquerade to :1024`</br>`masquerade to :1024-2048` |
