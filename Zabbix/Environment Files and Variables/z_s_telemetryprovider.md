# List of Variables:

| Variable | Options | Description |
| :---: | :---: | :--- |
| `ZBX_TELEMETRYPROVIDER_0=` | `(default none) \| <json configuration string>` | Variable used in Zabbix to configure telemetry data reporting. |
| `ZBX_TELEMETRYPROVIDER_0_USERNAME=` | `(default none) \| <username>` | Used to specify the username for the telemetry provider, which is responsible for sending anonymous telemetry data to help improve the system. |
| `ZBX_TELEMETRYPROVIDER_0_USERNAME_FILE=` | `(default none) \| path/to/file` | Specify the path to a file that contains the username for the telemetry provider in Zabbix. |
| `ZBX_TELEMETRYPROVIDER_0_PASSWORD=` | `(default none) \| <password>` | Used in Zabbix to specify the password for the telemetry provider. |
| `ZBX_TELEMETRYPROVIDER_0_PASSWORD_FILE=` | `(default none) \| path/to/file` | Specify the path to a file that contains the password for the telemetry provider in Zabbix. |
| `ZBX_TELEMETRYPROVIDER_0_SSL_KEY_PASSWORD=` | `(default none) \| <password>` | Used to store the password for the SSL key associated with the telemetry provider. |
| `ZBX_TELEMETRYPROVIDER_0_SSL_KEY_PASSWORD_FILE=` | `(default none) \| path/to/file` | Path to a file that contains the password for the SSL key associated with the telemetry provider in a containerized application. |

---
# Example of default .env file

```env
ZBX_TELEMETRYPROVIDER_0=
ZBX_TELEMETRYPROVIDER_0_USERNAME=
ZBX_TELEMETRYPROVIDER_0_USERNAME_FILE=
ZBX_TELEMETRYPROVIDER_0_PASSWORD=
ZBX_TELEMETRYPROVIDER_0_PASSWORD_FILE=
ZBX_TELEMETRYPROVIDER_0_SSL_KEY_PASSWORD=
ZBX_TELEMETRYPROVIDER_0_SSL_KEY_PASSWORD_FILE=
```
