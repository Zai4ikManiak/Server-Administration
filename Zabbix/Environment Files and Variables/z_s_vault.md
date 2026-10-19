# List of Variables:

| Variable | Options | Description |
| :---: | :---: | :--- |
| `ZBX_VAULT=` | `HashiCorp (default) \| CyberArk` | Specifies the vault provider. |
| `ZBX_VAULTAPPROLEID=` | `(default none) \| vault-id` | Specify the AppRole ID for authentication with HashiCorp Vault |
| `ZBX_VAULTAPPSECRETID=` | `(default none) \| vault-id` | Holds the identifier for a secret stored in a vault, such as Azure Key Vault. |
| `ZBX_VAULTDBPATH=` | `(default none) \| path/to/file` | Vault path or query, depending on the Vault, from where credentials for database will be retrieved by keys. |
| `ZBX_VAULTPREFIX=` | `(default none) \| global/path/to` | A custom prefix for Vault path or query, depending on the Vault. The most suitable defaults will be used if not specified. |
| `ZBX_VAULTURL=` | `https://127.0.0.1:8200 (default) \| https://vault_ip:8200` | The vault server HTTP(S) URL. The system-wide CA certificates directory will be used if SSLCALocation is not specified. |
| `VAULT_TOKEN=` | `(default none)` | The HashiCorp Vault authentication token that should have been generated exclusively for Zabbix server with read-only permission to the paths specified in Vault macros and read-only permission to the path specified in the optional `VaultDBPath` configuration parameter.</br>It is an error if `VaultToken` and `VAULT_TOKEN` environment variable are defined at the same time.</br></br>Mandatory: Yes, if Vault is set to HashiCorp; otherwise, no |
| `ZBX_VAULTTLSCERTFILE=` | `(default none) \| name-of-SSL-cert` | The name of the SSL certificate file used for client authentication.</br>The certificate file must be in PEM1 format.</br>If the certificate file contains also the private key, leave the SSL key file field empty.</br>The directory containing this file is specified by the configuration parameter SSLCertLocation.</br>This option can be omitted but is recommended for CyberArkCCP vault. |
| `ZBX_VAULTTLSKEYFILE=` | `(default none) \| ` | The name of the SSL private key file used for client authentication.</br>The private key file must be in PEM1 format.</br>The directory containing this file is specified by the configuration parameter SSLKeyLocation.</br>This option can be omitted but is recommended for CyberArkCCP vault. |

---
# Example of default .env file

```env
ZBX_VAULT=HashiCorp 
ZBX_VAULTAPPROLEID= 
ZBX_VAULTAPPSECRETID= 
ZBX_VAULTDBPATH= 
ZBX_VAULTPREFIX= 
ZBX_VAULTURL=https://127.0.0.1:8200
VAULT_TOKEN= 
ZBX_VAULTTLSCERTFILE= 
ZBX_VAULTTLSKEYFILE= 
```
