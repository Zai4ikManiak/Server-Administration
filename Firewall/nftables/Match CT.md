| Match Syntax | Examples |
| :---: | :--- |
| `state <state>` | `ct state { new, established, related, untracked }`</br>`ct state != related`</br>`ct state established`<br>`ct state 8` |
| `direction <value>` | `ct direction original`</br>`ct direction != original`</br>`ct direction { reply, original } ` |
| `status <status>` | `ct status expected`</br>`(ct status & expected) != expected`</br>`ct status { expected, seen-reply, assured, confirmed, snat, dnat, dying } ` |
| `mark [set]` | `ct mark 0`</br>`ct mark or 0x23 == 0x11`</br>`ct mark or 0x3 != 0x1`</br>`ct mark and 0x23 == 0x11`</br>`ct mark and 0x3 != 0x1`</br>`ct mark xor 0x23 == 0x11`</br>`ct mark xor 0x3 != 0x1`</br>`ct mark 0x00000032`</br>`ct mark != 0x00000032`</br>`ct mark 0x00000032-0x00000045`</br>`ct mark != 0x00000032-0x00000045`</br>`ct mark { 0x32, 0x2222, 0x42de3 }`</br>`ct mark { 0x32-0x2222, 0x4444-0x42de3 }`</br>`ct mark set 0x11 xor 0x1331`</br>`ct mark set 0x11333 and 0x11`</br>`ct mark set 0x12 or 0x11`</br>`ct mark set 0x11`</br>`ct mark set mark`</br>`ct mark set mark map { 1 : 10, 2 : 20, 3 : 30 }` |
| `expiration` | `ct expiration 30`</br>`ct expiration 30s`</br>`ct expiration != 233`</br>`ct expiration != 3m53s`</br>`ct expiration 33-45`</br>`ct expiration 33s-45s`</br>`ct expiration != 33-45`</br>`ct expiration != 33s-45s`</br>`ct expiration { 33, 55, 67, 88 }`</br>`ct expiration { 1m7s, 33s, 55s, 1m28s }` |
| `helper "<helper>"` | `ct helper "ftp"` |
| `[original | reply] bytes <value>` | `ct original bytes > 100000`</br>`ct bytes > 100000` |
| `[original | reply] packets <value>` | `ct reply packets < 100` |
| `[original | reply] ip saddr <ip source address>` | `ct original ip saddr 192.168.0.1`</br>`ct reply ip saddr 192.168.0.1`</br>`ct original ip saddr 192.168.1.0/24`</br>`ct reply ip saddr 192.168.1.0/24` |
| `[original | reply] ip daddr <ip destination address>` | `ct original ip daddr 192.168.0.1`</br>`ct reply ip daddr 192.168.0.1`</br>`ct original ip daddr 192.168.1.0/24`</br>`ct reply ip daddr 192.168.1.0/24` |
| `[original | reply] l3proto <protocol>` | `ct original l3proto ipv4` |
| `[original | reply] protocol <protocol>` | `ct original protocol 6` |
| `[original | reply] proto-dst <port>` | `ct original proto-dst 22` |
| `[original | reply] proto-src <port>` | `ct reply proto-src 53` |
| `count [over] <number of connections>` | `ct count over 2`</br>`tcp dport 22 add @ssh_flood { ip saddr ct count over 2 } reject`</br>`[ which requires an existing ssh_flood set, ie. add set filter ssh_flood { type ipv4_addr; flags dynamic; } ]` |
