| Match Syntax | Examples |
| :---: | :--- |
| `hdrlength <length>` | `ah hdrlength 11-23`</br>`ah hdrlength != 11-23`</br>`ah hdrlength { 11, 23, 44 }` |
| `reserved <value>` | `ah reserved 22`</br>`ah reserved != 33-45`</br>`ah reserved { 23, 100 }`</br>`ah reserved { 33-55 }` |
| `spi <value>` | `ah spi 111`</br>`ah spi != 111-222`</br>`ah spi { 111, 122 }` |
| `sequence <sequence>` | `ah sequence 123`</br>`ah sequence { 23, 25, 33 }`</br>`ah sequence != 23-33` |
