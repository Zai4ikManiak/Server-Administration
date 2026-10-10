| Match Syntax | Examples |
| :---: | :--- |
| `dscp <value>` | `ip dscp cs1`</br>`ip dscp != cs1`</br>`ip dcsp 0x38`</br>`ip dscp != 0x20`</br>`ip dscp { cs0, cs1, cs2, cs3, cs4, cs5, cs6, cs7, af11, af12, af13, af21, af22, af31, af32, af33, af41, af42, af43, ef }` |
| `length <length>` | `ip length 232`</br>`ip length != 233`</br>`ip length 333-435`</br>`ip length != 333-455`</br>`ip length { 333, 553, 673, 838}` |
| `id <id>` | `ip id 22`</br>`if ip != 233`</br>`ip id 33-45`</br>`ip id != 33-45`</br>`ip id { 33, 55, 67, 88}` |
| `frag-off <value>` | `ip frag-off & 0x1fff != 0 # match fragments`</br>`ip frag-off != 0 # match MF flag`</br>`ip frag-off & 0x400 != 0 # match DF flag` |
| `ttl <ttl>` | `ip ttl 0`</br>`ip ttl 233`</br>`ip ttl 33-55`</br>`ip ttl != 45-50`</br>`ip ttl { 43, 53, 45}`</br>`ip ttl { 33-55 }` |
| `protocol <protocol>` | `ip protocol tcp`</br>`ip protocol 6`</br>`ip protocol != tcp`</br>`ip protocol { icmp, eps, ah, comp, udp, udplite, tcp, dccp, sctp }` |
| `checksum <checksum>` | `ip checksum 13172`</br>`ip checksum 22`</br>`ip checksum != 233`</br>`ip checksum 33-45`</br>`ip checksum != 33-45`</br>`ip checksum { 33, 55, 67, 88 }`</br>`ip checksum { 33-55 }` |
| `saddr <ip source address>` | `ip saddr 192.168.2.0/24`</br>`ip saddr != 192.168.2.0/24`</br>`ip saddr 192.168.3.1 ip saddr 192.168.3.100`</br>`ip saddr != 1.1.1.1`</br>`ip saddr & 0xff == 1`</br>`ip saddr & 0.0.0.255 < 0.0.0.127` |
| `daddr <ip destination address>` | `ip daddr 192.168.0.1`</br>`ip daddr != 192.168.0.1`</br>`ip daddr 192.168.0.1-192.168.0.250`</br>`ip daddr 10.0.0.0-10.255.255.255`</br>`ip daddr 172.16.0.0-172.13.255.255`</br>`ip daddr 192.168.3.1-192.168.4.250`</br>`ip daddr != 192.168.0.1-192.168.0.250`</br>`ip daddr { 192.168.0.1-192.168.0.250 }`</br>`ip daddr { 192.168.5.1, 192.168.5.2, 192.168.5.3 }` |
