# List of Variables:

| Variable | Options | Description |
| :---: | :---: | :--- |
| `ZBX_DBTLSCONNECT=` | `(default none) | required | verify_ca | verify_full` | Setting this option to the following values enforces to use a TLS connection to the database.</br></br>`required` - connect using TLS;</br>`verify_ca` - connect using TLS and verify certificate;</br>`verify_full` - connect using TLS, verify certificate and verify that database identity specified by DBHost matches its certificate. |
| `ZBX_DBTLSCAFILE=` | `(default none) | yes (if DBTLSCONNECT= verify_ca or verify_full)` | The full pathname of a file containing the top-level CA(s) certificates for database certificate verification. |
| `ZBX_DBTLSCERTFILE=` | `(default none) | global/path/to/file` | The full pathname of a file containing the Zabbix server certificate for authenticating to database. |
| `ZBX_DBTLSKEYFILE=` | `(default none) | global/path/to/file` | The full pathname of a file containing the private key for authenticating to database. |
| `ZBX_DBTLSCIPHER=` | `(default none) | list-of-ciphers` | The list of encryption ciphers that Zabbix server permits for TLS protocols up through TLS v1.2.</br></br>Supported only for MySQL. |
| `ZBX_DBTLSCIPHER13=` | `(default none) | list-of-ciphers` | The list of encryption ciphersuites that Zabbix server permits for the TLS v1.3 protocol.</br></br>Supported only for MySQL, starting from version 8.0.16. |

# Example of default .env file

```env
ZBX_DBTLSCONNECT= 
ZBX_DBTLSCAFILE= 
ZBX_DBTLSCERTFILE= 
ZBX_DBTLSKEYFILE= 
ZBX_DBTLSCIPHER= 
ZBX_DBTLSCIPHER13= 
```
