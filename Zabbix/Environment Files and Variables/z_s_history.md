# List of Variables:

| Variable | Options | Description |
| :---: | :---: | :--- |
| `ZBX_HISTORYPROVIDER_<0-N>=` | `(default none) \| 'elasticsearch;value_types="str,log,text,json",url=http://elasticsearch:9200'` | Specify the history storage method for the Zabbix server, determining how historical data is managed and retrieved. |
| `ZBX_HISTORYPROVIDER_<0-N>_USERNAME=` | `(default none) \| <username>` | Specify the username for connecting to a history provider in a Zabbix container setup. |
| `ZBX_HISTORYPROVIDER_<0-N>_USERNAME_FILE=` | `(default none) \| path/to/file` | Specify a file that contains the username for connecting to the history provider in Zabbix.
| `ZBX_HISTORYPROVIDER_<0-N>_PASSWORD=` | `(default none) \| <password>` | Specify the username for connecting to a history provider in a Zabbix container setup. |
| `ZBX_HISTORYPROVIDER_<0-N>_PASSWORD_FILE=` | `(default none) \| path/to/file` | Specify a file that contains the password for connecting to the history provider in Zabbix.
| `ZBX_HISTORYPROVIDER_<0-N>_SSL_KEY_PASSWORD=` | `(default none) \| <password>` | Specify the password for the SSL key associated with the Zabbix history provider, which is essential for secure communication. |
| `ZBX_HISTORYPROVIDER_<0-N>_SSL_KEY_PASSWORD_FILE=` | `(default none) \| path/to/file` | Specify a file that contains the password for connecting for the SSL key associated with the Zabbix history provider. |

---
# Example of default .env file

```env
ZBX_HISTORYPROVIDER_<0-N>=
ZBX_HISTORYPROVIDER_<0-N>_USERNAME=
ZBX_HISTORYPROVIDER_<0-N>_USERNAME_FILE=
ZBX_HISTORYPROVIDER_<0-N>_PASSWORD=
ZBX_HISTORYPROVIDER_<0-N>_PASSWORD_FILE=
ZBX_HISTORYPROVIDER_<0-N>_SSL_KEY_PASSWORD=
ZBX_HISTORYPROVIDER_<0-N>_SSL_KEY_PASSWORD_FILE=
```
