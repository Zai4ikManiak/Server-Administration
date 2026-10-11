| Limit Statements | Description |
| :---: | :--- |
| `rate [over] <value> <unit> [burst <value> <unit>]` | `limit rate 400/minute`</br>`limit rate 400/hour`</br>`limit rate over 40/day`</br>`limit rate over 400/week`</br>`limit rate over 1023/second burst 10 packets`</br>`limit rate 1025 kbytes/second`</br>`limit rate 1023000 mbytes/second`</br>`limit rate 1025 bytes/second burst 512 bytes`</br>`limit rate 1025 kbytes/second burst 1023 kbytes`</br>`limit rate 1025 mbytes/second burst 1025 kbytes`</br>`limit rate 1025000 mbytes/second burst 1023 mbytes` |
