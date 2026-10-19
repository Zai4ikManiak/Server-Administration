# Zabbix Server and Web:

List of docker images:

| Zabbix component | Docker image | Description |
| :---: | :---: | :--- |
| **Server (MySQL)** | zabbix/zabbix-server-mysql | Central process of Zabbix software. |
| **Web interface (Nginx + MySQL)** | zabbix/zabbix-web-nginx-mysql | Used to manage resources under monitoring and view monitoring statistics. |

```bash
# Command structure
#
# <image> - zabbix element
# <os>-<X.X>-latest - Latest stable Zabbix version on the selected OS

docker pull zabbix/<image>:<os>-<X.X>-latest

# Example
docker pull zabbix/zabbix-server-mysql:ubuntu-7.4-latest
docker pull zabbix/zabbix-web-nginx-mysql:ubuntu-7.4-latest
```

---
## Server Deployment:

```bash
docker run \
    --name zabbix-server \
    --env-file zabbix_server.env \
    --init \
    -d zabbix/zabbix-server-mysql:7.4
```


