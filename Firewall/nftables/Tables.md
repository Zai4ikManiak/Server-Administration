# Syntax:

```bash
nft list tables [<family>]
nft [-n] [-a] list tble [<family>] <name>
nft (add | delete | flush) table [<family>] <name>

# [-n] -> shows the addresses and other information that use names in numeric format.
# [-a] -> used to display each rule's handle (i.e., a numeric identifier).
```

# Basic commands:

| Command | Description |
| :---: | :--- |
| `nft add table ip filter` | Additing tables. |
| `nft list tables` | Show/List tables. |
| `nft delete table ip filter` | Deleting tables. |
| `nft flush table ip filter` | Flushing tables.</br></br>This command will not flush sets defined within that table. |
