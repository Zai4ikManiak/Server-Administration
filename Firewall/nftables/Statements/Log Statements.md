| Statement Syntax | Examples |
| :---: | :--- |
| `level [over] <value> <unit> [burst <value> <unit>]` | `log`</br>`log level emerg`</br>`log level alert`</br>`log level crit`</br>`log level err`</br>`log level warn`</br>`log level notice`</br>`log level info`</br>`log level debug` |
| `group <value> [queue-threshold <value>] [snaplen <value>] [prefix "<prefix>"]` | `log prefix aaaaa-aaaaaa group 2 snaplen 33`</br>`log group 2 queue-threshold 2`</br>`log group 2 snaplen 33` |
